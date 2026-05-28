# Confidence Rating — 세그먼트·국가·결론별 신뢰도 등급

> CHECKER 가 검증을 마친 후, 각 세그먼트(또는 국가, 또는 핵심 결론) 에 4단계 중 하나의 confidence label 을 부여합니다. INTEGRATOR 가 국가 간 정렬 후 최종 등급을 확정합니다.

---

## 4단계 정의

| 등급 | 의미 | 발표 가능 범위 |
|---|---|---|
| **High** | CEO·이사회 보고에서 직접 인용 가능 | 외부 발표 OK, 숫자를 그대로 사용 가능 |
| **Medium** | 방향성은 옳음, 일부 추정 포함 | 내부 의사결정 OK, 외부 발표 시 caveat 필요 |
| **Low** | 지표성 (indicative) 만 | 내부 토론·가설 수립용. 외부 발표 시 정밀 검증 필수 |
| **Insufficient** | 자신 있게 제시할 수 없음 | "추가 리서치 필요" 로 명시. 숫자 제시 금지 |

---

## 부여 기준 (구체적 체크리스트)

### High — 다음을 **모두** 만족

- [ ] 시장 규모 데이터가 Tier S 또는 A
- [ ] 핵심 플레이어 정보가 Tier S–C 로 검증됨 (최소 2개 독립 소스)
- [ ] 모든 smell test 통과 (per-unit, cross-market, player sum)
- [ ] 데이터 시점이 2년 이내
- [ ] 단위·통화·기준일 명확
- [ ] CHECKER A 와 B 모두 통과
- [ ] 동일 또는 더 높은 티어의 모순되는 소스 없음

### Medium — 다음 **일부** 적용

- [ ] 시장 규모는 Tier E (자체 추정) 이지만 입력값이 모두 Tier S–C
- [ ] 플레이어 일부만 검증되고 일부는 Tier C–D
- [ ] Smell test 의 일부 통과 (1-2 개 항목 미진)
- [ ] 데이터 시점이 일부 2-3년 전
- [ ] 한 가지 소스에만 의존 (cross-reference 부족)

### Low — 다음 **하나 이상** 해당

- [ ] 시장 규모가 Tier E 인데 입력값 자체가 Tier D
- [ ] 플레이어 정보 대부분 Tier D–E
- [ ] Smell test 다수 미진 또는 미적용
- [ ] 데이터 시점 3년 이상
- [ ] 단일 소스 + cross-reference 불가

### Insufficient — 다음 **하나 이상** 해당

- [ ] 시장 규모를 추정할 입력값 자체가 부족하거나 Tier F
- [ ] 핵심 플레이어 식별 불가
- [ ] Smell test 모두 실패 (숫자가 비현실적)
- [ ] 데이터 자체가 5년 이상 전 + 최근 데이터 없음
- [ ] 사용 가능한 소스가 Tier D 이하만

---

## Confidence label 부착 규칙

1. **세그먼트별** 라벨 필수.
2. **국가별** 라벨도 별도 표기 (예: "한국 = High, 태국 = Medium").
3. 한 세그먼트 안에서 **항목별** 라벨이 다르면 가장 낮은 라벨로 통합 (보수적).
4. 라벨은 **모든 페이지·슬라이드·표** 에 표기. 첫 페이지에만 표기 후 생략 금지.
5. Insufficient 는 숨기지 않고 명시. "이 영역은 자신 있게 제시할 수 없습니다 — 추가 리서치 필요" 라고 적는 것이 더 신뢰를 만듭니다.

---

## 예시

```markdown
## 한국 외식업 SaaS 시장

**Confidence: High**
- 시장 규모: KRW 1,200억 (2024) — 출처: 한국정보산업연합회, Tier A
- 주요 플레이어: 토스플레이스, 캐치테이블, 페이히어 등 — 출처: DART 공시, Tier A + 업계 보도, Tier C
- 점유율: 토스플레이스 약 25% — Cross-reference 2개 (Statista Tier S, 매일경제 Tier C)

## 태국 외식업 SaaS 시장

**Confidence: Medium**
- 시장 규모: USD 80M (2024, 자체 추정) — 입력값: 사업체 수 (NSO, Tier A) × 채택률 (Statista, Tier S)
- 주요 플레이어: LMWN, FoodStory 등 — Tier C 매체 다수, 일부 회사 측 자료 (Tier B)
- 점유율 정밀 측정 어려움 → "LMWN 이 POS 영역에서 우세 (40%+)" 까지만 단언

## 라오스·캄보디아 외식업 SaaS

**Confidence: Insufficient**
- 사용 가능한 데이터가 Tier D 이하만 존재 (블로그·익명 매체)
- 추가 리서치 필요: 현지 정부 통계 확인, 현지 매체 직접 접촉
- 본 보고서에서는 제시하지 않음
```

---

## INTEGRATOR 가 국가 간 confidence 정렬

서로 다른 국가에서 같은 항목을 조사했을 때, 각 국가의 confidence 가 다를 수 있습니다. INTEGRATOR 는 다음을 적용:

1. 국가별 confidence 를 **별도로 유지** (한 줄에 묶지 않음).
2. **국가 간 비교 결론**을 낼 때는 가장 낮은 confidence 에 맞춤.
   - 예: 한국 시장 (High) + 태국 시장 (Medium) → 두 국가 비교는 Medium.
3. Insufficient 인 국가는 비교 분석에서 제외하고 명시.

---

## CRITIC 의 confidence 검증

CRITIC 단계에서 각 confidence label 을 다시 점검:

- "이 항목이 정말 High 인가? Tier S/A 만 사용했는가?"
- "Medium 으로 표기됐는데 실은 Low 가 아닌가?"
- "Insufficient 가 숨겨져 있지 않은가?"

CRITIC 의 마인드는 confidence 를 **한 단계씩 낮춰서** 다시 평가하는 것. 그래도 옳으면 통과, 의심되면 강등.

---

## 라벨 일관성 (PACKAGER)

PACKAGER 가 마지막에 점검:

- [ ] 모든 페이지·슬라이드에 confidence 라벨 표시되어 있나
- [ ] 라벨이 본문 데이터와 모순되지 않나 (High 인데 본문이 약하거나, Insufficient 인데 본문이 단언적이지 않나)
- [ ] Methodology page 에 라벨 부여 기준이 문서화되어 있나
