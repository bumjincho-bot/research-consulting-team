# Phase B — Units: 스코프 경계·분류·MECE 분해

> **다루는 단계**: 9-step generic sequence 의 3·4 단계 (Boundary + Decomposition)
> **목표**: 무엇이 IN / OUT 인지 잠그고, 답할 수 있는 하위 질문으로 MECE 분해. **분류 체계는 사용자와 함께 도출** (skill 이 미리 강요하지 않음).

---

## 1. 핵심 질문 (사용자에게 묻는 순서)

### Q6. IN / OUT Boundary
> **"무엇은 이 리서치에 반드시 포함됩니까? 무엇은 명시적으로 제외됩니까?"**

- 좋은 답: "IN: TW + TH 디지털 광고 중 LINE 이 운영하는 매체와 직접 경쟁하는 매체 / OUT: 비-디지털 (TV·OOH·Print), KR·JP 비교, 1차 조사"
- 나쁜 답: "다 보자" (boundary 없음)

> **원칙**: OUT 표기 없는 항목은 사용자가 묻지 않았다는 이유로 마음대로 빼지 않음. **명시적 제외만 OUT.**

### Q7. Decomposition Axis
> **"이 문제를 자르려면 어떤 기준이 가장 의미 있나요? 같은 답이 나와도 결정이 달라지는 차원이 뭡니까?"**

이게 v1.x 의 "FC1-FC6 어떻게 매핑할까?" 자리. 도메인을 가정하지 않고 사용자에게 직접 묻습니다. 가능한 차원 (다중 선택):

| 차원 | 예 |
|---|---|
| 산업·세그먼트 | 광고 카테고리 / 솔루션 유형 |
| 고객·청중 | LE / SME / Individual |
| 시간·주기 | FY24 / FY25 / FY26 |
| 지역·국가 | TW / TH |
| 제품·기술 | DSP / SSP / DMP |
| 채널·매체 | Search / Display / Message |
| 사용자 유형 | 광고주 / 매체사 / 에이전시 |
| 가치사슬 | 광고주 → 에이전시 → 매체 → 소비자 |

> **사용자가 "잘 모르겠다"** 면 Q7.5 로 분기.

#### Q7.5. 외부 표준 차용
> "사용자가 일하는 조직·산업에 이미 통용되는 분류 체계가 있습니까? (예: 작년 분석에 사용한 분류, 협회 분류, 정부 통계 분류, Wiki 표준)"

- "있다" → 그 분류 체계를 받아서 그대로 차용 (이번 디지털 광고 예시: EY 2024 Domain I·II 분류)
- "없다" → SCOPER 가 외부 7 프레임워크 중 한 두 개를 **예시**로 보여주고 사용자가 골라 만듦
- "재사용 가능한 패턴 있나요?" → `recurring-patterns/` 검토 → 매칭되면 "예시" 로만 제시 (강제 X)

### Q8. MECE Sub-Questions
> **"위 차원으로 자른 결과를 답할 수 있는 5–7 개 하위 질문으로 만들어 주세요."**

- 좋은 답:
  1. TW·TH 디지털 광고 시장 사이즈 by category? (Display/Search/Buzz/Message/RetailMedia)
  2. 카테고리별 LINE 점유율?
  3. LINE 보유 vs 미보유 세그먼트 매핑?
  4. FY26 forecast (성장률·외생 변수)?
  5. Top 광고주 분포 (Domain II)?
- 나쁜 답: "다 알아봐 주세요" (분해 안 됨)

> **MECE 검증**: 7개 가지가 (a) 서로 겹치지 않고 (mutually exclusive) (b) 합치면 원래 질문을 빠짐없이 덮는지 (collectively exhaustive) 점검. 안 맞으면 SCOPER 가 빠진 가지 / 겹치는 가지를 짚어 사용자에게 재확인.

### Q9. Segment Map
> **"각 하위 질문 × IN-scope 단위 (예: TW 카테고리 5개 × TH 카테고리 5개)** 의 매트릭스가 ANALYST 가 채울 마스터 체크리스트가 됩니다. 모든 셀에 처리 방침이 있어야 합니다."

```markdown
|       | Display | Search | Buzz | Message | RetailMedia |
|-------|---------|--------|------|---------|-------------|
| TW    | Phase 2 | Phase 2| Phase 2 | Phase 2 | Phase 2  |
| TH    | Phase 2 | Phase 2| Phase 2 | Phase 2 | Phase 2  |

— = 명시적 OUT
Phase 2 = ANALYST 가 데이터 수집
Stub = 데이터 부족 명시 후 부록 처리
```

---

## 2. SCOPER 가 답을 정리해 보여주는 템플릿

```markdown
## Phase B 정리 (사용자 승인 대기)

### B.1 IN / OUT Scope
- **IN**:
  - [Q6.in 항목들]
- **OUT** (명시적 제외):
  - [Q6.out 항목들 + 사유]

### B.2 분류 차원 (= 분석 단위)
- **선택된 차원**: [Q7 답]
- **분류 체계**: [Q7 답 + Q7.5 답]
- **차용 표준** (있으면): [예: EY 2024 Domain I·II 분류 / Wiki Criteria Clarification v10 / SIC code]
- **차용 시 검증 필요 사항**: [예: Audio/Podcast 매핑이 외부 표준에 없으면 부록 처리]

### B.3 MECE 하위 질문 (5–7 개)
1. [...]
2. [...]
...

### B.4 Segment Map (마스터 체크리스트)
[2D matrix]

---
**위 정리가 맞는지 확인 부탁드립니다. "Phase B 승인" 이라고 답해 주세요.**
```

---

## 3. Phase B 통과 체크

- [ ] Q6 답에 IN + OUT **둘 다** 명시
- [ ] Q7 답에 분류 차원 **하나 이상** 잠김
- [ ] Q8 답이 MECE (겹치지 않고 빠짐없는) 5–7 개 하위 질문
- [ ] Q9 segment map 의 **모든 셀에 처리 방침** (Phase 2 / OUT / Stub)
- [ ] 사용자 명시 승인

---

## 4. recurring-patterns 차용 시 SCOPER 발화 예시

```
"사용자께서 답해 주신 '디지털 광고 + 카테고리별 시장 사이즈' 패턴은
recurring-patterns/digital-advertising-ey-style.md 에 비슷한 분류가 있습니다.
이 snippet 의 5 카테고리 (Display / Search / Buzz / Message / RetailMedia) 를 
시작점으로 차용하시겠어요, 아니면 직접 새로 정의하시겠어요?

차용 시 장점: 이전 리서치와 비교 가능 / 검증 시간 단축
직접 정의 시 장점: 본 문제에 더 정확한 분류 가능
"
```

사용자 결정. SCOPER 는 강요하지 않음.

---

## 5. 흔한 함정

| 함정 | 왜 문제 |
|---|---|
| Q7 에서 SCOPER 가 SaaS 분류 (FC1-FC6) 를 자동 제시 | Phase A 에서 "광고 시장" 이라고 답했는데도 SaaS 분류를 끼워 넣으면 v1.x 의 같은 실패 반복 |
| Q8 의 MECE 검증을 생략 | 가지가 겹치면 ANALYST 가 같은 데이터를 두 번 모으고, 빠지면 답을 못 함 |
| OUT 표기 없는 항목을 SCOPER 마음대로 빼고 시작 | "묻지 않았다" 가 OUT 아님. 명시적 제외만 OUT |
| Q9 segment map 의 셀이 비어 있는데 Phase B 통과 처리 | ANALYST 가 진입 시 헤매게 됨 |

---

## 6. 외부 프레임워크 매핑 (참고)

| 외부 프레임워크 | 본 Phase B 와 매핑 |
|---|---|
| MECE / Issue Tree | Q7·Q8 의 핵심. "쪼개기" 가 본 phase 의 정체성 |
| Wardley Mapping | Q7 의 "가치사슬" 차원 옵션과 직결 |
| Cynefin | Q7.5 + Q8 에서 "도메인이 simple·complicated·complex 어느 쪽?" 사용자에게 묻고 분류 형태 조정 |
| Engagement-Letter | Q6 IN/OUT 잠금 자체가 contractual 성격 |

---

*Next: `Phase-C-metrics.md` (지표·단위·증거 기준)*
