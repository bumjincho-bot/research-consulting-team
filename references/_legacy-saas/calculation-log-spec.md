# Calculation Log Spec — 산출 로직 추적 표준

> ANALYST (Phase 2) 가 데이터를 수집하면서 **계산을 수행할 때마다** 기록하는 산출 로그.
> "이 숫자 어디서 왔어?" 에 역추적이 가능하도록 모든 중간 계산을 보존합니다.

---

## 1. 왜 필요한가

| 현재 (evidence-log.csv 만) | 추가 후 (+ calculation-log.csv) |
|---|---|
| 원시 데이터 (IR 매출, 가맹점 수) 만 기록 | 원시 데이터 **+ 중간 계산 과정** 기록 |
| "토스플레이스 F&B 매출 USD 38-50M" 의 근거 역추적 불가 | 입력값 → 공식 → 결과 체인 추적 가능 |
| CHECKER-A 가 smell test 할 때 원본 확인 어려움 | CHECKER-A 가 각 단계를 개별 검증 가능 |
| 다음 리서치에서 가정 변경 시 전체 재계산 필요 | 입력값 하나 바꾸면 영향 받는 결과 식별 가능 |

---

## 2. 파일 형식

### `calculation-log.csv` (per run 폴더에 저장)

| 컬럼 | 설명 | 예시 |
|---|---|---|
| `calc_id` | 계산 고유 번호 | C001 |
| `vertical` | 버티컬 | F&B |
| `solution` | 솔루션 카테고리 | Payment·POS |
| `player` | 회사명 (해당 시) | 비바리퍼블리카 |
| `description` | 무엇을 계산하는가 (한 줄) | 토스플레이스 F&B Payment·POS 귀속 매출 산정 |
| `formula` | 산출식 (사람이 읽을 수 있는 형태) | 전체 매출 × F&B 가맹점 비중 × SaaS 비율 |
| `inputs` | 입력값 (JSON 또는 파이프 구분) | E_total=2000억 \| ratio_fnb=0.68 \| ratio_saas=0.70 |
| `input_sources` | 각 입력값의 evidence-log ID 또는 출처 | E_total→E045(토스IR) \| ratio_fnb→E046(토스IR 2024-12) \| ratio_saas→자체추정 |
| `result` | 계산 결과 | 952억원 (USD 70M) |
| `range` | 오차 범위 (있으면) | USD 38-50M (±25%) |
| `confidence` | 계산 결과의 신뢰도 | Medium (ratio_saas 가 Tier E) |
| `used_in` | 이 결과가 쓰인 곳 | v1.4 § 3.1 매출 Share 표 → 토스플레이스 행 |
| `note` | 비고 | HW 제외 비율 70% 는 위키 § 0.4.2 기준 |

---

## 3. 기록 대상 (ANALYST 의무)

### 반드시 기록해야 하는 계산 유형

| 계산 유형 | 예시 | 기록 필요성 |
|---|---|---|
| **귀속 분배** | 토스플레이스 전체 매출 × F&B 68% | 필수 — 분배 비율 변경 시 모든 하위 결과 영향 |
| **Bottom-up 산정** | 사업체 수 × 채택률 × ARPU | 필수 — 3개 입력값 각각 역추적 필요 |
| **Solution 합산** | Queue + Booking + MO + Payment + Membership = 합계 | 필수 — 각 항목 개별 출처 연결 |
| **점유율 → 매출 환산** | 시장 규모 × 점유율% = 매출 | 필수 — 시장 규모·점유율 각각 출처 |
| **ARPU 역산** | 매출 ÷ 가맹점 수 = ARPU | 필수 — smell test 의 핵심 |
| **환율 환산** | KRW → USD | 기록 (단순하지만 환율 변경 시 영향 추적) |
| **HW/GMV 분리** | 전체 매출 − HW 매출 = SaaS 매출 | 필수 — 위키 § 0.4 기준 |
| **성장률 적용** | 2024 매출 × (1 + CAGR) = 2025F | 기록 |

### 기록 불필요 (단순 참조)

- 단순 데이터 인용 (출처 그대로 기재) → evidence-log 만으로 충분
- 단위 변환 (억원 → 만원) → 자명한 변환

---

## 4. 계산 체인 (Calculation Chain) 추적

복잡한 산출은 여러 단계를 거칩니다. `input_sources` 컬럼에 **다른 calc_id 를 참조** 할 수 있습니다:

```
C001: 토스플레이스 전체 매출 = 2,000억원 (출처: E045)
C002: F&B 가맹점 비중 = 68% (출처: E046)
C003: SaaS 비율 (HW 제외) = 70% (출처: 자체 추정, 위키 § 0.4.2)
C004: 토스플레이스 F&B SaaS 매출 = C001 × C002 × C003 = 952억원
C005: USD 환산 = C004 ÷ 1,360 = USD 70M
C006: F&B Payment·POS 시장 규모 = USD 188M × 45% = USD 80-110M (출처: E050)
C007: 토스플레이스 F&B Payment share = C005 ÷ C006 = ~25% (가맹점 기준)
```

→ `C007` 이 최종 보고서에 쓰인 "토스플레이스 25%" — 역추적하면 C005→C004→C001+C002+C003 → E045+E046+위키

---

## 5. CHECKER-A 의 활용

CHECKER-A (Phase 3a) 는 calculation-log 를 다음과 같이 검증:

1. **각 calc_id 의 formula 재계산** — inputs 넣어서 result 와 일치하는가?
2. **input_sources 유효성** — evidence-log ID 가 실재하는가? 값이 일치하는가?
3. **Smell Test** — 최종 result 가 상식적인가? (예: ARPU 가 100만원/년 수준인가?)
4. **체인 일관성** — 상위 calc_id 결과가 변경되면 하위도 변경 필요한지 체크

---

## 6. INTEGRATOR 의 활용

INTEGRATOR (Phase 4) 이중 산출 정합성 검증 시:
- 방법 A (Bottom-up) 의 calc_id 체인 합산 vs 방법 B (Solution 합) 의 calc_id 체인 합산
- 차이가 ±5% 초과 시 → 어느 calc_id 에서 차이가 발생하는지 추적

---

## 7. 적용 체크리스트

- [ ] ANALYST: 모든 계산 수행 시 calculation-log.csv 에 즉시 기록 (사후 기록 금지)
- [ ] ANALYST: formula 는 사람이 읽을 수 있는 형태로 작성 (코드 아님)
- [ ] ANALYST: input_sources 에 evidence-log ID 또는 다른 calc_id 필수 연결
- [ ] CHECKER-A: calculation-log 전체 재계산 검증
- [ ] INTEGRATOR: 이중 산출 정합성 시 calc_id 체인 비교
- [ ] PACKAGER: calculation-log.csv 를 run 폴더에 포함

---

## 8. 옵션 의존성

이 calculation-log 는 **옵션 A (이중 산출) 적용 시 의무**, 그 외에도 아래 조건에서 의무:

| 조건 | calculation-log 의무 |
|---|---|
| 옵션 A (이중 산출) ✅ | **필수** — 두 방법의 계산 체인 비교 필요 |
| 옵션 D (매출 Share) ✅ | **필수** — 매출 귀속 분배 계산 추적 |
| 방어 강도 High | **필수** — 모든 숫자 역추적 가능해야 |
| 방어 강도 Medium | **권장** — 핵심 숫자만 기록 |
| 방어 강도 Low | **선택** — ANALYST 판단 |
