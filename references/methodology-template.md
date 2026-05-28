# Methodology Template — 시장 사이징·리서치 방법론

> SCOPER 가 Phase 1 에서 **방법론 잠금** 을 할 때 사용하는 템플릿. 사용자에게 기존 방법론 표준이 없을 때 이 템플릿을 기반으로 새 방법론을 작성합니다. 한 번 잠그면 프로젝트 도중 변경 금지 (`personas/01-scoper.md` 참조).

---

## 사용 방법

1. SCOPER 가 사용자에게 "기존 방법론 표준이 있나요?" 질문
2. 있으면 그 문서 따름. 없으면 이 템플릿 복사 → 빈칸 채움
3. 채운 결과를 사용자에게 확인 → **명시적 승인 받기 전까지 ANALYST 진입 금지**
4. 승인된 방법론은 PACKAGER 단계에서 Methodology Page 의 기반이 됨

---

## 템플릿

### Section 1: 리서치 목표

- **핵심 질문**: [SCOPER brief 의 central question 그대로]
- **청중**: [CEO / 이사회 / 내부 / 클라이언트]
- **방어 강도**: [Low / Medium / High]
- **출력 형식**: [슬라이드 / 보고서 / 표 / 매트릭스]

---

### Section 2: 시장·산업 정의

#### 2.1 정의 범위

- **포함 (IN)**:
  - 사업 활동: ...
  - 비즈니스 타입: ...
  - 산업 분류 코드: ISIC Rev.4 [코드] / KSIC [코드] / JSIC [코드] / ROCSIC [코드] / TSIC [코드]

- **제외 (OUT)**:
  - 사업 활동: ...
  - 사유: ...

#### 2.2 세그먼테이션

- 세그먼트 1: [정의]
- 세그먼트 2: [정의]
- ...
- (세그먼트 간 중복·누락 점검 — MECE 원칙)

#### 2.3 다국가 정의 정렬 (해당 시)

| 국가 | 현지 분류 | ISIC 매핑 | 차이점 |
|---|---|---|---|
| KR | KSIC ... | ISIC ... | ... |
| JP | JSIC ... | ISIC ... | ... |
| TW | ROCSIC ... | ISIC ... | ... |
| TH | TSIC ... | ISIC ... | ... |

---

### Section 3: 시장 사이징 공식

#### 3.1 Top-Down 접근 (있을 시)

```
시장 규모 = 글로벌 시장 × 지역·국가 비중 × 세그먼트 비중
```

- 글로벌 시장: 출처 [Tier S 펌 또는 Tier A 국제기구]
- 지역·국가 비중: 출처 [...]
- 세그먼트 비중: 출처 [...]

#### 3.2 Bottom-Up 접근 (있을 시)

```
시장 규모 = 사업체 수 × 채택률 × 평균 연 지출
```

- **사업체 수**: 각국 통계청 (Tier A) — 어떤 census·연도 사용?
- **채택률**: Tier S 또는 자체 추정 (Tier E)
  - 자체 추정 시 입력값과 출처 명시
- **평균 연 지출**: Tier S 또는 비교 시장 inflate
  - 비교 시장 사용 시 환율·인플레·소득 조정 방법 명시

#### 3.3 사용할 접근

- [ ] Top-down only
- [ ] Bottom-up only
- [ ] 두 접근 cross-reference (권장)

---

### Section 4: 통화·환율 정책

- **기준 통화**: USD (또는 사용자 지정)
- **환율 기준일**: [YYYY-MM-DD]
- **환율 출처**: [World Bank / 한국은행 / IMF 등]
- **명목 vs PPP**:
  - [ ] 명목 환율 (외환 기준 시장 사이즈 비교)
  - [ ] PPP (구매력 비교)
- **사용 환율** (해당 시):
  - 1 USD = ___ KRW
  - 1 USD = ___ JPY
  - 1 USD = ___ TWD
  - 1 USD = ___ THB

---

### Section 5: 시점 정책

- **기준 연도**: [YYYY]
- **회계연도 vs 캘린더**:
  - [ ] 모두 캘린더 (1-12월) 로 환산
  - [ ] 각 국가 회계연도 그대로 (FY 표기)
- **데이터 시점이 국가별 다를 때**:
  - [ ] 가장 오래된 국가에 맞춤 (보수적)
  - [ ] 각 국가 최신으로 사용 (시점 명시)

---

### Section 6: 데이터 소스 우선순위

`references/source-tiers.md` 적용. 추가로 이 프로젝트의 우선 소스:

- 국가별 우선 소스: `references/countries/{kr,jp,tw,th,global}.md` 참조
- 유료 소스 사용 여부:
  - [ ] Statista
  - [ ] Mordor Intelligence
  - [ ] Yano Research (JP)
  - [ ] 資策會 MIC (TW)
  - [ ] Krungsri / SCB EIC / KResearch (TH)
  - [ ] (기타 추가)

---

### Section 7: Confidence Rating 기준

`references/confidence-rating.md` 적용. 이 프로젝트의 최소 confidence 기준:

- **방어 강도 High** (CEO/이사회): 핵심 결론 모두 confidence ≥ Medium 필요. High 권장.
- **방어 강도 Medium**: confidence ≥ Low 허용, 하지만 caveat 명시.
- **방어 강도 Low**: 모든 confidence 허용, 표기만 정확.

이 프로젝트의 방어 강도: [Low / Medium / **High**]

---

### Section 8: 검증 정책

- Cross-reference 최소 출처 수: [핵심 클레임당 2개 이상]
- Smell test 적용:
  - [ ] Per-Unit Test
  - [ ] Cross-Market Test
  - [ ] Player Sum Test
- Tier F 처리: 폐기 (예외 없음)
- 충돌 처리: 보수적 값 채택 + 범위 명시

---

### Section 9: 리스크와 가정 노출

이 방법론이 의존하는 핵심 가정:
1. ...
2. ...
3. ...

이 가정이 틀리면 결론에 미치는 영향:
- 가정 1 틀리면: ...
- 가정 2 틀리면: ...
- 가정 3 틀리면: ...

---

### Section 10: 변경 정책

- **잠금 후 변경 금지**: ANALYST 진입 후 방법론 변경 금지
- **개선 발견 시**: "next revision" 노트로 기록, 현재 프로젝트 소급 적용 X
- **변경 필요 시**: 사용자와 합의 후 전체 프로젝트 재시작

---

### 사용자 승인

```
[ ] 위 방법론에 동의합니다. ANALYST 단계로 진행해주세요.

승인일: [YYYY-MM-DD]
승인자: [이름]
```

---

## 변종 (방법론 패턴별)

### 패턴 A: 단일 국가, 단일 세그먼트 시장 사이징
- 위 템플릿 그대로 + 다국가 섹션 (2.3) 생략

### 패턴 B: 다국가 비교
- 모든 섹션 적용
- INTEGRATOR 가 정의·환율·시점 정렬 강도 높임

### 패턴 C: 경쟁 환경 매핑 (시장 사이징 없음)
- Section 3 (시장 사이징 공식) 생략
- 대신 "플레이어 식별 기준" + "점유율 추정 방법" 추가

### 패턴 D: 산업·버티컬 전반 분석
- 세그먼테이션 (2.2) 더 정밀
- 패턴 간 비교 프레임워크 (Section 5 strategic framework) 추가

### 패턴 E: Due Diligence
- Section 9 (리스크·가정) 강화
- 추가: 회사 실사 항목 (재무, 법무, 운영, 기술, 인사)

---

## 빠른 시작 (Minimal Methodology — Quick Brief 용)

방어 강도 Low 의 빠른 오리엔테이션이라면:

```markdown
## 방법론 (간략)

- 시장 정의: [한 문장]
- 시점: [YYYY]
- 통화: USD (환율 [출처])
- 사용 소스: [Tier S 펌 1-2개 + Tier A 정부 통계]
- Confidence 기준: 핵심 클레임 2개 출처
- 외부 발표 전 검증 필수
```

이 미니멀 방법론도 사용자 승인 받은 후 잠급니다.
