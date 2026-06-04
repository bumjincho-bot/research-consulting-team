# Phase C — Metrics: 지표·단위·증거 기준

> **다루는 단계**: 9-step generic sequence 의 5 단계 (Evidence)
> **목표**: 답을 어떤 숫자·지표로 표현할지 사용자와 함께 잠금. v1.x 의 "가맹점 수 / GMV" 처럼 SaaS 메트릭을 미리 강요하지 않음.

---

## 1. 핵심 질문

### Q10. Primary Metric
> **"답을 어떤 숫자·지표로 표현하면 의사결정에 가장 유용합니까?"**

분류 차원(Phase B)별로 메트릭이 다를 수 있습니다. 사용자에게 **분류별로** 묻습니다.

- 좋은 답: "카테고리별 ad spend (USD M, FY 단위)"
- 나쁜 답: "매출이요" (단위·시점 모호)

### Q11. Unit · Period · Reference Date
> **"그 지표의 단위·시점·기준일은 어떻게 정의됩니까? 통화는? 회계연도 vs 달력연도? 시점은 점·구간·평균 중 어느 것?"**

| 항목 | 받아낼 답 |
|---|---|
| 단위 | USD M / KRW B / count / % / bps / minutes ... |
| 시점 | FY24 (2024.04~2025.03) / CY2024 / 월별 / 분기별 / 시점 / 평균 |
| 기준일 | 발표일 / 회계연도 종료일 / 측정 시점 |
| 통화 환산 | FX rate 출처 + 환산 시점 (FY-end, 평균, spot) |

### Q12. Secondary / Cross-check Metric
> **"같은 답을 다른 방법으로도 산정할 수 있습니까? 그 두 값의 차이가 ±5% 이내면 검증된 것으로 봅니다 (Dual Sizing 원칙)."**

- 예: ad spend 를 "광고주 × 평균 spend" (Bottom-up) + "매체사 광고 매출 합" (Solution sum) 으로 두 번 산정
- 사용자가 "한 방법밖에 안 된다" 면 single sizing + caveat 명시

### Q13. Evidence Tier Threshold
> **"답에 들어가는 모든 숫자가 어느 신뢰도까지 허용됩니까?"**

| Tier | 출처 예시 | 용도 |
|---|---|---|
| S | 정부 통계, IPO 공시, 공식 IR | 핵심 숫자 |
| A | Tier-1 산업 리서치 (eMarketer, IDC 등 paid) | 핵심 숫자 |
| B | Tier-2 trade press, 협회 발표 | 보조 |
| C | 회사 self-disclosure, 블로그 | 부록·삼각검증 |
| D/E | 비공식 추정, 미공개 ARPU 가정 | 사용 금지 또는 명시적 caveat |

Phase A 의 Defensibility Bar 와 연동:
- High → S/A 우선, B/C 는 cross-check 만
- Medium → S/A/B 허용, C 는 cross-check 만
- Low → 모든 tier 허용

### Q14. "활성 / 유효" 정의 (해당 시)
> **"메트릭에 'active' / 'valid' / 'engaged' 같은 한정어가 있다면 어떻게 정의합니까?"**

이건 메트릭이 사용자·이벤트 기반일 때만 묻습니다 (예: "active advertiser = 최근 90일 내 광고비 지출 1USD 이상").

---

## 2. Phase C 정리 템플릿

```markdown
## Phase C 정리 (사용자 승인 대기)

### C.1 1차 지표 (Primary Metric)

| 분류 (Phase B) | 1차 지표 | 단위 | 시점 |
|---|---|---|---|
| Display | Ad spend | USD M | FY24 / FY25E / FY26F |
| Search | Ad spend | USD M | FY24 / FY25E / FY26F |
| Message | Ad spend | USD M | FY24 / FY25E / FY26F |
| ... | ... | ... | ... |

### C.2 단위·기준일·환율
- **통화**: USD M (TW NTD, TH THB → FY-end FX rate 변환)
- **회계연도**: 일본 FY (FY26 = 2026.04 ~ 2027.03)
- **FX 출처**: BOT (TH), CBC (TW)

### C.3 2차 지표 / Cross-check
- **Bottom-up**: 광고주 × 평균 ad spend × 매체별 비중
- **Solution-sum**: 매체사 광고 매출 공시 합산
- **검증 기준**: ±5% 이내

### C.4 Evidence Tier Threshold
- **수용 tier**: S, A, B (C 는 cross-check 만)
- **Defensibility 와의 정합**: Phase A 의 High 와 일치

### C.5 "활성 / 유효" 정의 (있으면)
- [정의]

---
**"Phase C 승인" 이라고 답해 주세요.**
```

---

## 3. Phase C 통과 체크

- [ ] Q10 답에 분류별 1차 지표 명시
- [ ] Q11 답에 단위 + 시점 + 기준일 + 통화 환산 명시
- [ ] Q12 답에 cross-check 방법 명시 (또는 single sizing 사유)
- [ ] Q13 답에 Tier threshold 명시 (Phase A Defensibility 와 정합)
- [ ] (해당 시) Q14 답에 "활성 / 유효" 정의 명시

---

## 4. 흔한 함정

| 함정 | 왜 문제 |
|---|---|
| 분류별 메트릭이 다를 수 있는데 "매출 USD" 하나로 통합 | 광고비·구독료·거래액·라이선스가 모두 다름. 각 분류의 표준 메트릭을 따로 잠가야 함 |
| FY-CY 변환 protocol 미정 | INTEGRATOR 단계에서 한꺼번에 변환하다 오류 발생. 본 phase 에서 변환 방식 (proportional / quarter-weighted / source-quoted) 잠금 |
| Tier C 를 핵심 숫자에 사용하면서 Defensibility High 라고 표시 | 모순. Defensibility 와 Tier threshold 정합 검증 필수 |
| "활성 / 유효" 한정어를 받지 않고 ANALYST 단계 진입 | 회사별 정의 다름. 비교 불가능해짐 |
| Cross-check 없이 single sizing 을 묵시적 default | Dual Sizing 원칙 위배. 사용자에게 명시적으로 single sizing 수용 여부 확인 |

---

## 5. 외부 프레임워크 매핑

| 프레임워크 | 본 Phase C 와 매핑 |
|---|---|
| Toulmin (claim-grounds-warrant) | Q10·Q12·Q13 = 무엇을 grounds 로 쓸지 잠금 |
| Heilmeier (How will you measure success?) | Q10·Q11 직접 차용 |
| Hypothesis-Driven (S6) | Q12 Cross-check 가 가설 검증 형식과 정합 |

---

*Next: `Phase-D-methodology.md` (스타일 7개 + 방법론 합의)*
