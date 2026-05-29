# Multi-Session Protocol — 다중 세션 리서치 운영 표준

> 대규모 리서치 (Large 등급: 6+ 세그먼트, 3+ 국가, 방어 강도 High) 는 **단일 OpenCode 세션의 컨텍스트 한계**(약 200K 토큰)를 초과합니다. 이 문서는 리서치를 여러 세션으로 분할하면서도 방법론·잠금사항·산출물 일관성을 유지하는 표준 프로토콜을 정의합니다.
>
> 이 패턴은 실제 4국 × 6 Vertical Customer-facing SaaS 리서치 (run `2026-05-29-customer-facing-saas-tw-th-kr-jp`) 에서 검증되었습니다.

---

## 1. 언제 다중 세션을 적용하는가

### 자동 적용 (Large 등급)
다음 조건 중 **하나라도** 해당하면 다중 세션이 사실상 필수입니다:

- 세그먼트 수 ≥ 6 (예: 6개 Vertical)
- 국가 수 ≥ 3
- 방어 강도 = **High** (CEO/이사회/투자자)
- 옵션 A·B·C·D·E·F 중 **3개 이상** 동시 적용
- ANALYST 단계 예상 evidence-log 행 ≥ 200

### 권장 적용 (Medium 등급)
- 세그먼트 수 3-5 + 국가 2개
- 방어 강도 Medium 이상

### 미적용 (Small 등급)
- 단일 세그먼트 + 단일 국가 + 방어 강도 Low/Medium → 단일 세션 충분

---

## 2. 세션 분할 표준 (3가지 패턴)

### 패턴 1: 단일 국가 표준 (3 세션)

방어 강도 Medium, 단일 국가, 3-5 세그먼트:

| 세션 | Phase | 산출물 |
|---|---|---|
| **#1 Setup** | SCOPER | brief.md, methodology.md, session-log.md |
| **#2 Data** | ANALYST + CHECKER-A·B | evidence-log.csv, calculation-log.csv |
| **#3 Output** | INTEGRATOR + ARCHITECT + CRITIC + WRITER + GATEKEEPER + PACKAGER | findings, weak-points, final-report |

### 패턴 2: 다국가 순차 표준 (5-7 세션)

방어 강도 High, 2-4 국가, Dual Sizing:

| 세션 | Phase | 산출물 추가 |
|---|---|---|
| **#1 Setup** | SCOPER | brief.md, methodology.md, session-log.md |
| **#2 Data (국가 1)** | ANALYST + CHECKER-A·B | evidence-log.csv (국가 1 행), calculation-log.csv (국가 1 행) |
| **#3 Data (국가 2)** | ANALYST + CHECKER-A·B | (위 파일 append) |
| **#4 Data (국가 N)** | ANALYST + CHECKER-A·B | (위 파일 append) |
| **#N-1 Synthesis** | INTEGRATOR + ARCHITECT + CRITIC | findings-summary.md, weak-points-register.md, confidence-by-segment.md |
| **#N Output** | WRITER + GATEKEEPER + PACKAGER | final-report.md, what-worked.md, what-failed.md |

> **국가 우선순위**: 사용자 결정 사항. 데이터 가용성 높은 국가 먼저 진행 권장 (방법론 안정성 검증 기회).

### 패턴 3: 단일 국가 분할 표준 (4 세션)

방어 강도 High, 단일 국가, 6+ 세그먼트:

| 세션 | Phase | 산출물 |
|---|---|---|
| **#1 Setup** | SCOPER | brief.md, methodology.md |
| **#2 Data Part 1** | ANALYST (세그먼트 1-3) + CHECKER-A·B | evidence-log.csv (Part 1) |
| **#3 Data Part 2** | ANALYST (세그먼트 4-6) + CHECKER-A·B | evidence-log.csv (Part 2 append) |
| **#4 Synthesis + Output** | INTEGRATOR + ARCHITECT + CRITIC + WRITER + GATEKEEPER + PACKAGER | final-report.md |

---

## 3. 표준 산출물 (Run 폴더 구조)

다중 세션 운영을 위한 run 폴더는 다음 파일을 표준 산출물로 갖습니다:

```
learning-log/runs/{YYYY-MM-DD}-{topic-slug}/
├── brief.md                    # 세션 #1 SCOPER (잠금됨)
├── methodology.md              # 세션 #1 SCOPER (잠금됨)
├── session-log.md              # ⭐ 모든 세션이 매번 업데이트
├── NEXT-SESSION-GUIDE.md       # ⭐ 다음 세션 부트스트랩 메시지 템플릿
├── evidence-log.csv            # ANALYST 단계 시작 시 헤더만 생성 → 매 세션 append
├── calculation-log.csv         # ANALYST 단계 시작 시 헤더만 생성 → 매 세션 append
├── findings-summary.md         # Synthesis 세션 출력
├── weak-points-register.md     # Synthesis 세션 출력
├── confidence-by-segment.md    # Synthesis 세션 출력
├── what-worked.md              # 누적 (모든 세션이 발견 시 append)
├── what-failed.md              # 누적
├── next-revision-notes.md      # 누적
└── final-report.md             # Output 세션 출력
```

⭐ 표시 = 다중 세션 패턴에서 신규로 정의된 표준 산출물.

---

## 4. session-log.md 표준 양식

### 4.1 파일 구조

```markdown
# Session Log — {Topic}

> Run ID: {run-id}
> Purpose: 세션 간 핸드오프 기록. **새 세션 시작 시 가장 먼저 이 파일을 읽고 직전 세션의 마지막 항목을 확인할 것**.

---

## 세션 #1 — {Phase Name} ({YYYY-MM-DD}) {✅ or ⏳}

### 진행 페르소나
- ORCHESTRATOR
- {Phase 페르소나}

### 완료된 작업
- [x] ...
- [x] ...

### 미완료 — 다음 세션 시작 전 필수
- [ ] ...

### 핵심 결정 사항 (잠금 — 변경 금지)

| 항목 | 결정 |
|---|---|
| ... | ... |

### 산출물 위치
- ...

### 다음 세션 (#N) 시작 절차
1. ORCHESTRATOR 도입
2. cat session-log.md → 직전 세션 핸드오프 메시지 확인
3. cat brief.md, methodology.md → 잠금사항 재확인
4. ...

### 핸드오프 메시지 (다음 세션이 첫 번째로 읽을 것)

```
✅ 세션 #N ({Phase}) 완료.
다음 세션이 시작되면:
1. ...
2. ...
```

---

## 세션 #2 — {Phase Name} (예정)
> 세션 시작 시 이 섹션을 채울 것.
```

### 4.2 매 세션 종료 시 의무 사항

세션을 종료하기 전 **반드시** 다음을 `session-log.md` 에 기록:

- [ ] 진행 페르소나
- [ ] 완료된 작업 체크리스트
- [ ] 미완료 작업 (다음 세션 인계 사항)
- [ ] 핵심 결정 사항 (잠금)
- [ ] 산출물 위치
- [ ] **다음 세션 시작 절차** (cat 명령 + 페르소나 진입 순서)
- [ ] **핸드오프 메시지** (다음 세션이 처음 읽을 메시지)
- [ ] 세션 종료 시각

---

## 5. NEXT-SESSION-GUIDE.md 표준 양식

새 OpenCode 세션 시작 시 사용자가 채팅창에 붙여넣을 메시지 템플릿. 매 세션 종료 시 **다음 세션용 가이드를 미리 작성**해둡니다.

### 5.1 구조

```markdown
# 🚀 다음 세션 시작 가이드 — 세션 #{N+1} ({Phase Name})

> 이 파일은 **새 OpenCode 세션 시작 시 가장 먼저 사용자가 보내는 메시지의 템플릿**입니다.
> 새 세션 채팅창에 아래 메시지 박스를 그대로 붙여넣으면 ORCHESTRATOR가 즉시 {Phase}로 진입합니다.

---

## 📋 새 세션 시작 시 사용자가 붙여넣을 메시지

```
research-consulting-team 세션 #{N+1} ({Phase Name}) 시작합니다.

직전 세션 (#{N} {이전 Phase})에서 {핵심 산출물}이 작성되었습니다.

Run 폴더: {절대 경로}

읽어야 할 파일 (순서대로):
1. session-log.md — 직전 세션 상태와 핸드오프 메시지
2. brief.md — Research Brief (잠금된 스코프)
3. methodology.md — 방법론 (잠금됨, 변경 금지)
4. {Phase별 우선 reference 파일}
5. {그 외 필요한 reference}

{Phase Name} 시작:
- {구체적 진입 절차}
- {산출물 추가 위치}

방어 강도 {Level} + {적용된 옵션 모두 명시} 모드입니다.
```

---

## 🎯 세션 #{N+1} {Phase}의 작업 범위

{Phase별 세부 작업 정의}

### Quality Gate (세션 #{N+1} 종료 조건)
- [ ] ...

---

## 🔐 새 세션이 자동 점검할 잠금 사항

| 항목 | 잠금 값 | 변경 금지 사유 |
|---|---|---|
| ... | ... | ... |

> 변경 시도 발견 시: 즉시 중단 + 사용자에게 "방법론 잠금 위반, 변경 시 전체 프로젝트 재시작 필요" 보고.

---

## 📞 직전 세션 (#{N}) 완료 사항 요약

- ✅ ...
```

### 5.2 매 세션 종료 시 의무 사항

다음 세션을 위한 NEXT-SESSION-GUIDE.md를 **현 세션 종료 전 반드시 작성** 또는 갱신.

---

## 6. 세션 시작 의식 (Rotation Ritual)

새 세션을 열 때마다 ORCHESTRATOR가 **반드시 가장 먼저 수행**하는 절차:

### 6.1 부트스트랩 6단계

```
1. cd {run-folder-path}

2. cat session-log.md
   → 직전 세션 핸드오프 메시지 확인
   → 미완료 항목 체크

3. cat brief.md
   → 잠금된 핵심 질문·스코프 재확인
   → 사용자 승인 여부 확인 (head의 Status 라인)

4. cat methodology.md
   → 잠금된 방법론 재확인
   → 변경 금지 사항 메모리에 적재

5. cat NEXT-SESSION-GUIDE.md (있다면)
   → 직전 세션이 작성한 진입 절차 확인
   → 이번 세션의 작업 범위 명확화

6. wc -l evidence-log.csv calculation-log.csv (있다면)
   → 누적 데이터 진척 확인
```

### 6.2 잠금 사항 자동 점검

세션 시작 시 ORCHESTRATOR는 다음을 자동 점검:

- 본 세션이 잠금된 방법론을 변경하려는 시도가 없는가
- 본 세션이 brief.md의 스코프를 벗어나려 하지 않는가
- 본 세션이 적용 옵션 (A·B·C·D·E·F)을 변경하려 하지 않는가

> **위반 시도 발견 시**: 즉시 중단 + 사용자에게 "방법론 잠금 위반, 변경 시 전체 프로젝트 재시작 필요" 보고.

### 6.3 사용자에게 한 줄 요약 보고

부트스트랩 완료 후 사용자에게 다음 형식으로 보고:

```
✅ 세션 #{N} 부트스트랩 완료.
- Run: {run-id}
- 직전 세션 #{N-1}: {Phase} ({완료 / 일부 완료})
- 누적 evidence: {N}행, calculation: {M}행
- 본 세션 목표: {Phase} ({핵심 작업})
- 잠금 점검: ✅ 통과

{Phase} 단계로 진입합니다.
```

---

## 7. CSV 헤더 사전 생성 패턴

ANALYST 단계 시작 시 evidence-log.csv 와 calculation-log.csv를 매번 새로 생성하면 컬럼 정의 오류·중복 헤더 위험이 있습니다.

### 7.1 SCOPER 세션 종료 시 (Phase 1)

세션 #1 SCOPER 종료 직전 다음을 수행:

```python
import csv

evidence_header = ['id','vertical','data_point','value','unit','year','source','tier','url_or_report','license_note','fetch_date','status','checker_note']
with open('evidence-log.csv', 'w', encoding='utf-8', newline='') as f:
    csv.writer(f).writerow(evidence_header)

calc_header = ['calc_id','vertical','solution','player','description','formula','inputs','input_sources','result','range','confidence','used_in','note']
with open('calculation-log.csv', 'w', encoding='utf-8', newline='') as f:
    csv.writer(f).writerow(calc_header)
```

### 7.2 이후 세션은 append만

이후 모든 세션은 **헤더 없이 append만** 수행. 헤더 중복 검출 시 즉시 중단.

```python
import csv
with open('evidence-log.csv', 'a', encoding='utf-8', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(['E001', 'F&B', '...', ...])
```

---

## 8. 잠금 사항 변경 금지 프로토콜

### 8.1 잠금되는 항목 (변경 시 전체 프로젝트 재시작 필요)

| 카테고리 | 항목 | 잠금 위치 |
|---|---|---|
| 정의 | 분석 단위 (Product/Solution) | brief.md, methodology.md § 1 |
| 정의 | 산업 분류 (ISIC 매핑) | methodology.md § 2.3 |
| 통화 | 표준 통화 (USD 또는 사용자 지정) | methodology.md § 4 |
| 통화 | 환율 출처 (IMF IFS 등) | methodology.md § 4 |
| 시점 | 기준 연도 정책 | methodology.md § 5 |
| 옵션 | 적용된 옵션 (A·B·C·D·E·F 중 어떤 것) | brief.md 옵션 메뉴 |
| 옵션 | 방어 강도 | brief.md, methodology.md § 1 |
| 소스 | Tier F 사용 금지 | methodology.md § 8.3 |
| 스코프 | IN / OUT 경계 | brief.md |

### 8.2 변경 가능한 항목 (next-revision-notes.md 에 기록 후 다음 run 적용)

- 새로 발견된 검색 키워드 (what-worked.md)
- 신뢰 못한 소스 (what-failed.md)
- 방법론 개선 후보 (next-revision-notes.md)
- ANALYST 의 데이터 수집 우선순위
- Insufficient 셀의 추가 조사 시도

### 8.3 변경 시도 발견 시

매 세션 시작 의식 (§ 6.2) 에서 자동 점검. 위반 발견 시:

1. 즉시 작업 중단
2. 사용자에게 보고: "방법론 잠금 위반: {위반 항목}. 변경하시려면 전체 프로젝트 재시작이 필요합니다. 또는 next-revision-notes.md에 기록 후 다음 run에 적용하시겠습니까?"
3. 사용자 결정 대기

---

## 9. 컨텍스트 사용 추정

### 9.1 세션당 안전 작업량 (200K 토큰 기준)

| 작업 | 추정 토큰 |
|---|---|
| SCOPER (brief + methodology + session-log) | ~30K |
| ANALYST 1 국가 1 Vertical (Standard) | ~15K |
| ANALYST 1 국가 6 Vertical (Standard) | ~80-100K |
| CHECKER-A·B 1 국가 | ~30-50K |
| INTEGRATOR 4국 정렬 | ~50K |
| ARCHITECT + CRITIC | ~40K |
| WRITER + GATEKEEPER + PACKAGER | ~60K |

### 9.2 안전 마진

세션당 최대 사용량을 **150K 토큰**으로 제한 권장. 50K 마진은:
- 이전 메시지 누적
- 디스크에서 읽은 reference 파일들
- 다음 페르소나 진입 시 새 컨텍스트 로딩

### 9.3 한도 초과 신호

다음 신호 발견 시 **즉시 세션 종료 + 다음 세션으로 인계**:

- "Context limit reached" 경고
- 응답 속도 현저히 느려짐 (페르소나 컨텍스트 과부하)
- 동일 reference를 5번 이상 다시 읽어야 함

---

## 10. 다중 세션 vs 단일 세션 선택 의사결정

```
질문: 이 리서치는 단일 세션으로 가능한가?

1. 세그먼트 수 ≥ 6? → YES → 다중 세션
2. 국가 수 ≥ 3? → YES → 다중 세션
3. 방어 강도 = High? → YES → 다중 세션 권장
4. ANALYST 예상 evidence-log 행 ≥ 200? → YES → 다중 세션
5. 옵션 A·B·C·D·E·F 중 3개 이상 적용? → YES → 다중 세션 권장
6. 위 모두 NO → 단일 세션 가능

다중 세션 결정 시:
- 세션 분할 패턴 선택 (§ 2)
- run 폴더 + session-log.md + NEXT-SESSION-GUIDE.md 구조 준비
- 세션 #1 SCOPER 종료 시 CSV 헤더 사전 생성 (§ 7)
```

---

## 11. 사용자 커뮤니케이션 표준

### 11.1 첫 인터뷰 시 (SCOPER)

다중 세션 가능성을 SCOPER 단계에서 사용자에게 알림:

```
이번 리서치는 {Large} 등급으로 분류됩니다 ({사유}).
단일 세션으로 끝내기 어려워 {N}세션 분할을 권장합니다.

세션 분할:
- 세션 #1 (지금): SCOPER — brief + methodology 작성, 사용자 승인
- 세션 #2-#{M}: ANALYST + CHECKER (국가별 또는 세그먼트별)
- 세션 #{M+1}: INTEGRATOR + ARCHITECT + CRITIC
- 세션 #{N}: WRITER + GATEKEEPER + PACKAGER

각 세션 끝에 NEXT-SESSION-GUIDE.md 가 자동 생성되어, 다음 세션에서 그대로 붙여넣기만 하면 됩니다.
```

### 11.2 세션 종료 시

```
✅ 세션 #{N} ({Phase}) 종료.

이번 세션 산출물:
- {산출물 1}
- {산출물 2}

누적 진척:
- evidence-log.csv: {N}행 (status=VERIFIED: {V}, REJECTED: {R}, RAW: {R})
- calculation-log.csv: {M}행

다음 세션 시작:
1. 새 OpenCode 세션 열기
2. {Run폴더}/NEXT-SESSION-GUIDE.md 의 메시지 박스를 그대로 붙여넣기
3. ORCHESTRATOR가 자동으로 {다음 Phase}로 진입

(이 메시지는 session-log.md에도 저장됨)
```

---

## 12. 적용 체크리스트

다중 세션 운영 시 매 세션마다 다음을 확인:

### 세션 시작 시
- [ ] cat session-log.md → 직전 핸드오프 확인
- [ ] cat brief.md → 잠금 스코프 확인
- [ ] cat methodology.md → 잠금 방법론 확인
- [ ] cat NEXT-SESSION-GUIDE.md → 진입 절차 확인 (있다면)
- [ ] 잠금 사항 변경 시도 점검
- [ ] 사용자에게 한 줄 요약 보고

### 세션 진행 중
- [ ] 모든 데이터 → evidence-log.csv 즉시 append
- [ ] 모든 계산 → calculation-log.csv 즉시 기록
- [ ] 컨텍스트 한도 모니터링 (§ 9)
- [ ] 잠금 사항 위반 발생 시 즉시 중단

### 세션 종료 시
- [ ] session-log.md 업데이트 (진행/완료/미완료/핸드오프)
- [ ] NEXT-SESSION-GUIDE.md 작성 또는 갱신
- [ ] 누적 산출물 통계 사용자 보고
- [ ] 다음 세션 진입 절차 명확히 제시

---

## 13. 참고 — 본 프로토콜이 검증된 run

- `learning-log/runs/2026-05-29-customer-facing-saas-tw-th-kr-jp/` — 4국 × 6 Vertical, 방어 강도 High, 옵션 A·B·C·D·E·F 전체 적용. 7세션 분할 (패턴 2).

향후 다른 Large 등급 run에서 본 프로토콜이 추가 검증될 때마다 이 섹션에 append.
