# Classification Framework — 이중 분류 체계 가이드 (v1.8)

> SCOPER (Phase 1) 가 분류 체계를 잠글 때, ANALYST (Phase 2) 가 표를 작성할 때 참조.
> v1.8 (2026-05-29): Wiki Criteria Clarification v10 의 **Funnel × Function 이중축 분리** 반영.

---

## ⚠️ v1.8 변경 사항 (2026-05-29) — Wiki v10 정합

기존 v1.3-v1.4 (KR SaaS) 에서는 "Function (F1-F6)" 단일축으로 사용했으나, Wiki v10 (2026-05-26 업데이트) 에서 **Funnel** (소비자 경험 분석용) 과 **Function** (매출 귀속용) 이 명확히 분리됐습니다.

| 축 | 코드 | 의미 | 용도 | 관계 |
|---|---|---|---|---|
| **Funnel (구. F1-F6)** | FN1-FN6 | 소비자 여정 시간 순서 (Discovery → Retention) | 소비자 경험 분석, Lock-in 평가, 진입 기회 발굴 | N:N |
| **Function (신규)** | FC1-FC6 | 시장에 실재하는 SaaS 상품 카테고리 | 매출 귀속, 시장 규모 산출, 점유율 산정 | N:N |

**기존 KR/TW/TH 보고서의 "F1-F6" 라벨은 "FN1-FN6 Funnel"로 리라벨**해야 wiki v10과 정합됩니다. 매출 귀속용 카테고리는 별도로 FC1-FC6 매핑을 추가합니다.

---

## 0. Funnel (FN1-FN6) — 소비자 여정 분석

| 코드 | Funnel | 정의 |
|---|---|---|
| **FN1** | Discovery | 소비자가 매장/서비스를 인지·탐색·비교 |
| **FN2** | Scheduling | 소비자가 시간/순서/자원 슬롯을 확보 |
| **FN3** | Ordering | 소비자가 상품/서비스를 선택·지정 |
| **FN4** | Payment | 소비자가 대가를 지불 |
| **FN5** | Fulfillment | 소비자가 주문 결과를 수령 |
| **FN6** | Retention | 거래 완료 후 관계 유지·재방문 |

### Funnel 보유 판별 기준 (C1+C2+C3 모두 충족)

| 조건 | 정의 |
|---|---|
| **C1. 소비자 접점** | 소비자가 직접 조작하는 UI 또는 소비자에게 직접 전달되는 아웃풋이 있는가? |
| **C2. 솔루션 자체 제공** | 솔루션 내장 또는 솔루션이 직접 제공하는 모듈/애드온인가? |
| **C3. 현재 제공 중** | 베타 미출시·서비스 종료가 아닌가? |

### Funnel 활용처

- 소비자 경험의 끊김 없는 커버리지 분석 ("LINE MAN이 FN1+FN2+FN3+FN5+FN6 = 5/6 커버")
- 플랫폼 Lock-in 평가 (Funnel 커버리지 넓을수록 가맹점·소비자 이탈 어려움)
- 진입 기회 발굴 ("매출은 큰데 FN3 가 끊기는 vertical?")
- **매출 귀속에는 사용하지 않음** (그건 FC 의 역할)

---

## 1. Function (FC1-FC6) — 매출 귀속 + 시장 사이징

| 코드 | Function | 정의 | 해당 상품 예시 |
|---|---|---|---|
| **FC1** | POS / 결제 | 매장 내 거래를 처리하는 판매시점 관리 및 결제 솔루션 | iCHEF, FoodStory, 토스플레이스, JERA Cloud, Square |
| **FC2** | Mobile Order / 주문 | 소비자가 모바일·웹으로 상품/서비스를 주문하는 솔루션 | QR 스캔 주문, LINE 주문, 외송 주문 접수, 微碧 |
| **FC3** | Booking / 예약 | 소비자가 시간·자원 슬롯을 확보하는 예약·대기 솔루션 | inline, 캐치테이블, GoWabi, Mindbody |
| **FC4** | Membership / 회원·CRM | 가맹점의 고객 관계를 관리하고 재방문을 유도하는 솔루션 | Ocard, Dodo Point, 12CM, LINE OA |
| **FC5** | Delivery / 배달 | 소비자에게 상품을 배달하는 과정을 관리하는 솔루션 | 배민 사장님앱, Grab Merchant, LINE MAN Merchant |
| **FC6** | Discovery / 탐색 | 소비자가 매장/서비스를 검색·비교·발견하는 플랫폼 | Wongnai, Klook, KKday, ClassPass |

### Function 귀속 판정 (Product Identity 기준)

> **"솔루션이 스스로를 어떤 카테고리로 정의하는가?"** 가 우선. 키워드:

| 코드 | 키워드 |
|---|---|
| FC1 POS | POS, 收銀, 결제 시스템, payment system, 카드 단말, 수납 |
| FC2 Mobile Order | 주문, 點餐, ordering, 외송 접수, QR 주문, 모바일 오더 |
| FC3 Booking | 예약, 訂位, booking, reservation, 候位, 대기, queue |
| FC4 Membership/CRM | 회원, CRM, 集點, loyalty, 멤버십, 고객 관리, 쿠폰, 재방문 |
| FC5 Delivery | 배달, 外送, delivery, 라이더, 물류, 픽업 |
| FC6 Discovery | 탐색, 검색, 맛집, 추천, 리뷰, 평점, 找餐廳, restaurant guide |

### Function 활용처

- 시장 규모 산출 (Vertical × Function 매출 합계)
- 매출 귀속 (솔루션의 매출을 어떤 상품 카테고리에 넣을지)
- 점유율 산출 (Function 별 시장 내 솔루션 간 매출/가맹점 비율)

### Function 별 metric 등급 (Wiki v10 신규)

각 매출 수치는 다음 셋 중 하나로 태깅:

| 등급 | 표기 | 적용 조건 |
|---|---|---|
| **실측** | (실측) | Tier A/B 출처에서 직접 확인 가능 |
| **추정** | (추정) | 공개 데이터 기반 산식 적용 (가맹점 수 × ARPU 등) |
| **산출 불가** | — | 번들·비공개로 추정도 불가 |

**추정 시 의무 표기**: 산식 (예: "6,000점 × ¥4,167/월 × 12") + 입력값 출처 (각각).

### Function 별 표 출력 형식

| 국가 | Vertical | Solution | Function | 매출 (USD M) | 매출 등급 | 가맹점 수 | 가맹점 등급 | GMV | GMV 등급 | 거래 건수 | 추정 산식 | 입력값 출처 | 비고 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TW | F&B | iCHEF | FC1 POS | 12-13 | 실측 | 15,000 | 실측 | — | — | — | — | 91APP IR (NTD 1.619B) | 기본 구독료 귀속 |
| TW | F&B | iCHEF | FC2 Mobile Order | 2-3 | 추정 | 8,000 | 추정 | — | — | 월 100만 건 | 월 600TWD × 8,000점 × 12 | 가맹점: 전체 15K × 53% / 모듈가: 공식 요금표 | 이중 추정 |

---

## 2. Funnel × Function N:N 매핑 (Wiki v10)

하나의 Function은 여러 Funnel을 커버하고, 하나의 Funnel을 여러 Function이 담당. **N:N 관계**.

| | FN1 Discovery | FN2 Scheduling | FN3 Ordering | FN4 Payment | FN5 Fulfillment | FN6 Retention |
|---|---|---|---|---|---|---|
| **FC1 POS / 결제** | | | | ◉ | | |
| **FC2 Mobile Order** | | | ◉ | ● | | |
| **FC3 Booking / 예약** | | ◉ | ● | | | |
| **FC4 Membership / CRM** | | | | | | ◉ |
| **FC5 Delivery / 배달** | | | | | ◉ | |
| **FC6 Discovery / 탐색** | ◉ | | | | | |

> ◉ = 해당 Function의 주력 Funnel 단계. ● = 부수적으로 커버.

---

## 3. 이중 분류 원칙: Solution Rows + Funnel + Function

이전 (v1.3-v1.4): "Solution Rows + F1-F6"
**현재 (v1.8)**: "Solution Rows = FC1-FC6 매핑 + FN1-FN6 Funnel 별도 매트릭스"

| 축 | 역할 | 예시 |
|---|---|---|
| **1차 분류 (Primary)** = Solution Rows | 시장 규모·점유율·매출 산출의 기본 단위 (= FC1-FC6 매핑) | F&B Cloud POS = FC1, Mobile Order = FC2 ... |
| **보조 분류 (Secondary)** = Funnel Matrix | 소비자 경험 커버리지 평가 + 진입 기회 발굴 | FN1-FN6 Y/N matrix per player |

---

## 4. 1차 분류 채택 기준 (우선순위 순)

### 기준 1: 데이터 가용성 (최우선)

| 평가 | 정의 | 채택 기준 |
|---|---|---|
| ✅ High | Tier A·B 출처에서 직접 확인 가능 | 1차 분류 후보 |
| ⚠️ Medium | Tier B·C cross-reference 추정 가능 | 보조 분류 |
| ❌ Low | Tier D·E ±25% 이상 오차 | 채택 불가 — 부록 보존 |

**판정법**: "이 분류 단위로 시장 규모 산정 시 출처의 Tier 분포가 Tier A·B 70%+ 인가?"

### 기준 2: 청중 적합성

- CEO/이사회: "이 시장에 진출할 가치가 있는가?" → **Function (FC) 단위** 유용
- CTO/R&D: "Funnel 갭은 어디인가?" → **Funnel (FN) 매트릭스** 유용
- 기본값 (CEO/이사회): 1차 = Solution Rows / Function (FC), 보조 = Funnel (FN)

### 기준 3: 위키/팀 표준 호환

- Wiki v10 backbone 정의가 있으면 **Funnel + Function 둘 다 반드시 포함**
- Wiki snapshot policy 준수 (`references/wiki-snapshot-policy.md`)

---

## 5. 미채택 분류 처리 (부록 보존 의무)

검토 후 채택하지 않은 분류 체계는 **부록에 반드시 보존**.

### KR/TW/TH SaaS 에서 미채택된 분류 3개

| 분류 | 데이터 가용성 | 청중 적합성 | 미채택 사유 |
|---|---|---|---|
| Front vs Back-of-house | ❌ Low | ⚠️ Medium | 스코프 중복 (Front 만 다룸) |
| B2B vs B2C | ❌ Low | ⚠️ Medium | 양면 시장 — 같은 회사가 양쪽 |
| Stack-based (FE/BE/Infra) | ❌ Low | ❌ Low | Vertical SaaS 와 Layer 직교 |

---

## 6. 적용 체크리스트 (v1.8)

- [ ] SCOPER: Wiki snapshot fetch (`wiki-snapshot-policy.md`)
- [ ] SCOPER: 분류 축 2개 (Funnel + Function) 후보 도출
- [ ] SCOPER: 데이터 가용성 평가 매트릭스 작성
- [ ] SCOPER: 1차·보조 확정 + 미채택 분류 보존 계획
- [ ] ANALYST: Solution Rows 기준 표 작성 + FC 매핑 명시 + FN 매트릭스 병기
- [ ] ANALYST: 매출 수치 = 실측/추정/산출 불가 등급 명시
- [ ] INTEGRATOR: 1차·보조 합 정합성 ±5% 검증
- [ ] WRITER: F1-F6 표현 사용 금지 — FN1-FN6 (Funnel) 또는 FC1-FC6 (Function) 명시
- [ ] PACKAGER: 부록에 미채택 분류 + Wiki snapshot 메타데이터 + 채택 사유 종합 매트릭스 포함

---

## 7. 마이그레이션 가이드 (v1.4 → v1.8)

기존 KR v1.4 보고서의 "F1-F6" 표현을 v1.8로 전환할 때:

| 기존 (v1.4) | 신규 (v1.8) | 비고 |
|---|---|---|
| "F1 Discovery" | "FN1 Discovery" + "FC6 Discovery / 탐색" | Funnel과 Function 분리 |
| "F2 Scheduling" | "FN2 Scheduling" + "FC3 Booking / 예약" | — |
| "F3 Ordering" | "FN3 Ordering" + "FC2 Mobile Order / 주문" | — |
| "F4 Payment" | "FN4 Payment" + "FC1 POS / 결제" | — |
| "F5 Fulfillment" | "FN5 Fulfillment" + "FC5 Delivery / 배달" | — |
| "F6 Retention" | "FN6 Retention" + "FC4 Membership / CRM" | — |
| "F1-F6 Function 매트릭스" | "FN1-FN6 Funnel 매트릭스" + "FC1-FC6 Function 매핑" | 두 표 분리 |
| "Solution Rows" | "Solution Rows (FC1-FC6 매핑)" | FC 매핑 컬럼 추가 |

**중요**: F1-F6의 "Function" 의미와 FC1-FC6의 "Function" 의미는 **다르다**. 전자는 v1.8 기준 "Funnel"로 재명명되었고, 후자는 신규 매출 귀속 카테고리.
