# Evidence Log Spec — 데이터 수집·검증 추적 표준

> ANALYST (Phase 2) 가 데이터를 수집할 때마다 **즉시** 기록하는 원시 데이터 로그.
> CHECKER (Phase 3) 가 검증 결과를 `status` 컬럼에 기록.
> WRITER (Phase 7) 는 `status == VERIFIED` 인 항목만 보고서에 사용.

---

## 1. 설계 원칙 (Option A: 단일 파일 + status 컬럼)

- **단일 파일** `evidence-log.csv` 에 수집·검증·폐기 이력 모두 보존
- **실시간 append** — ANALYST (또는 서브 에이전트) 가 데이터 발견 즉시 기록
- **CHECKER 가 status 업데이트** — RAW → VERIFIED / REJECTED / SUPERSEDED
- **히스토리 보존** — 삭제 없음. REJECTED 도 남김 (CEO "왜 안 썼어?" 답변용)
- **WRITER 필터** — `status == VERIFIED` 만 보고서 인용 가능

---

## 2. 컬럼 구조

| 컬럼 | 설명 | 예시 |
|---|---|---|
| `id` | 고유 번호 (E001~) | E049 |
| `vertical` | 버티컬 | F&B |
| `data_point` | 수집한 사실 (한 줄) | iCHEF TW active merchants |
| `value` | 수치 | 15000-16000 |
| `unit` | 단위 | stores |
| `year` | 데이터 시점 | 2024 |
| `source` | 출처명 | iCHEF official website |
| `tier` | 소스 Tier (S/A/B/C/D/E/F) | B |
| `url_or_report` | 원본 URL 또는 리포트 ID | ichefpos.com/zh-tw/about-ichef |
| `license_note` | 라이선스 | Public |
| `fetch_date` | 접근일 | 2026-05-27 |
| `status` | 검증 상태 | RAW / VERIFIED / REJECTED / SUPERSEDED |
| `checker_note` | CHECKER 판정 메모 (있을 때만) | Smell test passed: ARPU TWD 23,400/yr matches pricing |

---

## 3. Status 정의

| Status | 의미 | 설정 주체 | 보고서 사용 가능 |
|---|---|---|---|
| **RAW** | ANALYST 가 수집, 아직 미검증 | ANALYST | ❌ (CHECKER 대기) |
| **VERIFIED** | CHECKER-A + CHECKER-B 모두 통과 | CHECKER | ✅ 사용 가능 |
| **REJECTED** | CHECKER 검증 실패 (부정확·outdated·신뢰 불가) | CHECKER | ❌ (사유 기록) |
| **SUPERSEDED** | 더 신뢰도 높은 데이터로 대체됨 | CHECKER | ❌ (대체 ID 기록) |

---

## 4. 워크플로우

```
ANALYST 수집 (status=RAW)
  → evidence-log.csv 에 즉시 append
  → 서브 에이전트도 직접 append 가능 (파일 동시 쓰기 허용)

CHECKER-A (숫자 검증)
  → evidence-log.csv 읽기
  → smell test 수행
  → status 를 RAW → VERIFIED 또는 REJECTED 로 업데이트
  → checker_note 에 판정 사유 기록

CHECKER-B (출처 검증)
  → URL 실재 확인, 시점 2년 이내 확인
  → VERIFIED 유지 또는 REJECTED 로 변경

WRITER
  → evidence-log.csv 에서 status=VERIFIED 만 필터
  → 보고서에 인용 시 evidence ID (E001 등) 명시
```

---

## 5. 서브 에이전트 append 규칙

서브 에이전트가 직접 evidence-log.csv 에 쓸 때:
- 반드시 `status=RAW` 로 기록
- 기존 파일 끝에 append (기존 데이터 수정 금지)
- 동일 데이터 중복 수집 시 → 둘 다 기록 (CHECKER 가 판단)
- 파일 잠금 없음 (CSV append 는 atomic 하지 않으므로 줄 단위 완결성 유지)

---

## 6. 모순 데이터 처리

같은 사실에 대해 다른 값이 나올 때:
```csv
E049,F&B,iCHEF revenue,7.5,USD M,2024,GetLatka,C,getlatka.com,Public,2026-05-27,RAW,
E050,F&B,iCHEF revenue (implied from acquisition),12.8,USD M,2024,91APP acquisition P/S 2.5x,A,ir.91app.com,Public,2026-05-27,RAW,
```

CHECKER 판정 후:
```csv
E049,F&B,iCHEF revenue,7.5,USD M,2024,GetLatka,C,getlatka.com,Public,2026-05-27,SUPERSEDED,Replaced by E050 (higher tier source)
E050,F&B,iCHEF revenue (implied from acquisition),12.8,USD M,2024,91APP acquisition P/S 2.5x,A,ir.91app.com,Public,2026-05-27,VERIFIED,Tier A > Tier C; consistent with monthly fee × merchant count
```

---

## 7. 적용 조건

| 조건 | evidence-log status 컬럼 의무 |
|---|---|
| 방어 강도 High | **필수** |
| 방어 강도 Medium | **필수** |
| 방어 강도 Low | 권장 (status 생략 가능, 전부 VERIFIED 간주) |

---

## 8. 적용 체크리스트

- [ ] ANALYST: 모든 데이터 수집 시 evidence-log.csv 에 status=RAW 로 즉시 append
- [ ] ANALYST (서브 에이전트): 동일 규칙 — 직접 파일 append 허용
- [ ] CHECKER-A: evidence-log.csv 전체 읽기 → smell test → status 업데이트
- [ ] CHECKER-B: URL 확인 → status 업데이트
- [ ] WRITER: status=VERIFIED 만 인용 (REJECTED/SUPERSEDED 인용 시 GATEKEEPER 반려)
- [ ] PACKAGER: evidence-log.csv 최종본에 RAW 남아있으면 반려 (모든 항목 판정 완료 필수)
