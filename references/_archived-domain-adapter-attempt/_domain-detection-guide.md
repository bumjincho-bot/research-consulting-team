# Domain Detection Guide — SCOPER 의 주제→어댑터 매핑 로직

> **사용 시점**: SCOPER (Phase 1) 가 사용자로부터 리서치 주제를 받자마자 첫 번째로 수행하는 단계.
> **목적**: 주제에서 트리거 키워드를 추출해 적합한 도메인 어댑터를 후보로 제시하고 사용자에게 선택을 받습니다.
> **버전**: v2.0 (2026-06-04 신설)

---

## 1. 핵심 원칙

1. **자동 결정 금지** — 트리거 매칭이 명확해도 사용자에게 "이 어댑터로 진행할까요?" 라고 반드시 묻습니다.
2. **다중 매칭 허용** — 한 주제가 여러 어댑터에 매칭되면 모두 제시 (예: "fintech SaaS for restaurants" → fintech + saas-vertical 둘 다).
3. **Fallback 명시** — 매칭이 없으면 `_generic` 어댑터를 권장하되 신규 어댑터 작성 가능성도 안내.
4. **사용자 override 우선** — 사용자가 "X 어댑터로 해" 라고 지시하면 매칭 무시하고 그대로 사용.

---

## 2. 트리거 키워드 매트릭스

각 어댑터의 트리거 키워드는 어댑터의 `README.md` 에서 가져옵니다. 본 가이드는 **빠른 매칭용 인덱스**입니다.

| 어댑터 | 한국어 트리거 | 영어 트리거 | 분야 표지 |
|---|---|---|---|
| **saas-vertical** | SaaS, 버티컬, 가맹점, 매장, POS, 멤버십, 예약 시스템, 배달 SaaS | SaaS, vertical SaaS, merchant, storefront, POS, booking, restaurant tech, retail tech | "솔루션이 가맹점에 매월 구독료" 형태 |
| **digital-advertising** | 디지털 광고, 광고 시장, 광고비, 매체, 미디어 바이, LAP, 공식계정 광고, 스폰서드 스티커, programmatic, retail media | digital advertising, ad spend, media buy, programmatic, DSP, SSP, ad network, retail media | "광고주가 매체에 광고비 지출" 형태 |
| **fintech** | 핀테크, 결제, 송금, BNPL, 대출, 카드사, 페이, 인슈어테크 | fintech, payment, remittance, BNPL, lending, card, insurtech, neobank | "거래액 × 수수료율" 형태 |
| **healthcare-it** | 헬스케어 IT, EMR, 원격진료, 의료 데이터, 디지털 치료제, telehealth | EMR, EHR, telehealth, DTx, digital therapeutics, healthcare IT | "의원 수 / 환자 수 × ARPU" 형태 |
| **ecommerce-platform** | 이커머스, 온라인 쇼핑, 마켓플레이스, 셀러 SaaS | e-commerce, marketplace, online retail, seller platform | "GMV × take rate" 형태 |
| **_generic** | (매칭 없음 / 사용자 정의) | (any) | (도메인 표지 모호 또는 신규) |

---

## 3. 매칭 알고리즘 (SCOPER 가 따라야 할 단계)

```
[Input]: 사용자 주제 텍스트 (예: "TW·TH 디지털 광고 시장 + LINE 포지션")

Step 1. 주제 텍스트를 lowercase + 한국어/영어 양쪽으로 토큰화
Step 2. 각 어댑터의 트리거 키워드와 부분 매칭 (substring) 수행
Step 3. 매칭 점수 계산:
   - 정확 매칭 (whole-word): +3점
   - 부분 매칭 (substring): +1점
   - 분야 표지 (예: "광고비 지출") 매칭: +5점
Step 4. 점수 ≥ 3 인 어댑터를 후보로 선정
Step 5. 후보가 0개 → _generic 권장
       후보가 1개 → 그 어댑터를 추천으로 표시
       후보가 2개 이상 → 모두 제시 + "조합 사용 가능" 안내
```

### 매칭 예시

| 주제 | 매칭된 키워드 | 후보 어댑터 |
|---|---|---|
| "TW·TH 디지털 광고 시장 + LINE 포지션 + FY26 forecast" | 디지털 광고 (+3), 광고 시장 (+3), LAP/OA (+1) | **digital-advertising** (점수 7) |
| "한국 F&B 6-vertical SaaS 시장" | SaaS (+3), vertical (+3), F&B (+1) | **saas-vertical** (점수 7) |
| "BNPL fintech for SMB merchants" | BNPL (+3), fintech (+3), merchant (+3) | **fintech** + **saas-vertical** (조합) |
| "EMR 시장 + 원격진료 도입률" | EMR (+3), 원격진료 (+3) | **healthcare-it** (점수 6) |
| "Vertical AI agent 시장" | (매칭 없음) | **_generic** (fallback) |
| "Shopify 셀러 plugin 생태계" | seller platform (+3), e-commerce (+3) | **ecommerce-platform** (점수 6) |

---

## 4. SCOPER 가 사용자에게 보낼 메시지 템플릿

### Case A: 단일 어댑터 매칭

```markdown
## 도메인 어댑터 식별

주제 분석 결과, 이 리서치는 **`<adapter-name>`** 도메인 어댑터에 가장 적합합니다.

### 어댑터 표준 미리보기
- **분류 체계**: <classification.md 의 1차 분류 요약>
- **1차 지표**: <metrics.md 의 핵심 지표>
- **방법론 옵션**: <methodology-options.md 의 옵션 코드 목록>
- **권장 출처**: <source-candidates.md 가 있으면 요약>

### 어떻게 진행할까요?

[A] 추천 어댑터 그대로 사용 (`<adapter-name>`)
[B] 다른 어댑터 사용 (목록: ...)
[C] 어댑터 미사용 — `_generic` 으로 직접 정의
[D] 어댑터 조합 (예: `<adapter-name>` + 다른 어댑터의 일부 요소)
```

### Case B: 다중 어댑터 매칭

```markdown
## 도메인 어댑터 식별 — 복수 후보

주제가 여러 도메인에 걸쳐 있어 다음 어댑터들이 후보입니다:

1. **`<adapter-1>`** (점수 X) — <왜 매칭됐는지>
2. **`<adapter-2>`** (점수 Y) — <왜 매칭됐는지>

### 권장 진행

각 어댑터의 강점이 보완 관계에 있으므로 다음 중 선택해 주세요:

[A] 주 어댑터 = `<adapter-1>`, 보조로 `<adapter-2>` 의 일부 요소 (예: 메트릭만)
[B] 주 어댑터 = `<adapter-2>`, 보조로 `<adapter-1>`
[C] 양쪽 모두 미사용 — `_generic` 으로 직접 정의
```

### Case C: 매칭 없음 → _generic

```markdown
## 도메인 어댑터 식별 — 매칭 없음

주제에서 기존 어댑터 트리거 키워드를 찾지 못했습니다. 두 가지 경로가 있습니다:

[A] **`_generic` 어댑터 사용** — Dual Sizing (Option A) 만 기본 ON, 분류·메트릭·기타 옵션은 사용자가 직접 정의
[B] **신규 어댑터 작성** — 향후 같은 도메인 리서치가 반복될 예정이라면 `references/domain-adapters/<new-domain>/` 신설 권장. 작성은 SCOPER 가 인터뷰를 통해 도와드립니다.

선택해 주세요.
```

---

## 5. 어댑터 결정 후 SCOPER 가 잠가야 할 항목

사용자가 어댑터를 확정한 뒤, SCOPER 는 다음을 Research Brief 에 명시적으로 기록합니다:

| 항목 | 예시 |
|---|---|
| **Active Adapter** | `digital-advertising` |
| **Adapter Version** | v2.0 |
| **Selected Methodology Options** | A, C, D, G, H |
| **Override Notes** | (있다면 사용자가 어댑터 표준에서 변경한 부분) |

이 정보는 ANALYST 핸드오프 메시지에 그대로 전달됩니다 (`personas/01-scoper.md` 의 핸드오프 템플릿 참조).

---

## 6. 어댑터 미정의 시 사용자 의사 결정 절차

```
사용자가 [B] 신규 어댑터 작성 선택 시:

1. SCOPER 가 신규 어댑터 인터뷰 시작:
   - 도메인명 확정 (kebab-case, 예: "supply-chain-saas")
   - 트리거 키워드 5개 이상
   - 1차 분류 체계 (예: 어떤 카테고리들로 시장을 자르나)
   - 1차 지표 (시장 규모 산정의 기본 단위)
   - 적합/부적합 청중

2. SCOPER 가 어댑터 4개 핵심 파일 초안 작성 (README, classification, metrics, methodology-options)

3. 사용자 승인 후 references/domain-adapters/<new-domain>/ 에 저장

4. _domain-detection-guide.md 에 트리거 키워드 추가

5. 정상 SCOPER 흐름 (Research Brief, Methodology Lock, Segment Map) 으로 복귀
```

---

## 7. 적용 체크리스트

- [ ] SCOPER 가 사용자 주제 받자마자 본 가이드 정독
- [ ] 트리거 키워드 매칭 수행 → 점수 계산
- [ ] 사용자에게 후보 어댑터 제시 + 선택 요청
- [ ] 사용자 승인 후 Research Brief 에 Active Adapter 명시
- [ ] ANALYST 핸드오프 메시지에 어댑터 경로 + 선택된 옵션 포함
- [ ] (신규 어댑터 작성한 경우) 본 가이드 트리거 키워드 표 업데이트

---

*End of Domain Detection Guide. Next: choose an adapter and read its `classification.md`, `metrics.md`, `methodology-options.md`.*
