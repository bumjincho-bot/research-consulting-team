# Phase D — Methodology: 리서치 스타일 + 방법론 합의

> **다루는 단계**: 9-step generic sequence 의 6·7 단계 (Method + Risk)
> **목표**: 사용자가 자기 문제에 맞는 **리서치 스타일** 을 고르고, 그 스타일에 맞는 분석 방법·검증 방식·리스크를 합의. 회사·기관 이름이 아닌 **방향성** 으로 표현.

---

## 1. 리서치 스타일 (7개) — 사용자에게 보여줄 표

회사·기관 이름은 **부록 C** 에 메타데이터로만 보관. 사용자에게는 방향성과 적합 상황만 보여줍니다.

| 코드 | 스타일 | 한 문장 방향성 | 적합 상황 | 단점·주의 |
|---|---|---|---|---|
| **S1** | Issue Decomposition | 큰 질문을 겹치지 않는 5–7 하위 질문으로 쪼개고, 가지별 답을 종합 | 시장 사이징 / 진입 전략 / 다각도 분석 | 가지 수가 많으면 깊이 부족 |
| **S2** | Decision-Centered | "이 답이 어떤 결정을 바꾸나?"부터 묻고 결정에 필요한 최소 증거만 수집 | M&A / 투자 판단 / GO·NO-GO | 결정과 무관한 인접 인사이트 누락 가능 |
| **S3** | Question-Refinement | 막연한 토픽 → 초점 토픽 → 답할 수 있는 질문 → "So what?" → 연구 문제 | 신규 영역 / 문제 정의 자체가 미정 | 답 도출보다 문제 정의에 시간이 더 듦 |
| **S4** | Interactive Design | Goal · Framework · Question · Method · Validity 동시 설계, 한 요소 변하면 전체 재조정 | 정성 분석 / 조직·문화 / 비구조화 문제 | 정량 사이징 사용 시 비효율 |
| **S5** | Engagement-Letter | Services · Term · Deliverable · Exclusion · Owner · Cost 를 먼저 계약적으로 고정 | 클라이언트 컨설팅 / 다자간 협업 | scope 변경 비용 큼 (문서 갱신 의무) |
| **S6** | Hypothesis-Driven | 가설을 먼저 세우고, 그것을 지지·반박하는 증거만 수집 | 정책 영향 평가 / A/B / 인과 검증 | 가설 외 발견 누락 가능 |
| **S7** | Context-First | 문제의 맥락 (simple / complicated / complex / chaotic) 을 먼저 파악, 거기에 맞는 분석 선택 | 도메인 미정 / 신규 카테고리 / 모호 문제 | 메타-분석 단계 추가로 시간 소요 |

> **단독 또는 조합** 가능. 예: `S2 + S6` = "결정 중심 + 가설 기반"

---

## 2. 핵심 질문

### Q15. Style Selection
> **"위 7개 스타일 중 본 리서치에 가장 가까운 것은 무엇입니까? 단독·조합 모두 가능합니다."**

스타일 결정 후 SCOPER 가 그 스타일의 **Phase 2 운영 의무** 를 사용자에게 설명하고 합의받습니다 (다음 표 참조).

#### 스타일별 ANALYST 추가 의무

| 스타일 | ANALYST 가 추가로 해야 하는 것 |
|---|---|
| **S1** | MECE 트리의 모든 가지 답을 채움. 빠진 가지 발견 시 SCOPER 재인터뷰 트리거 |
| **S2** | 결정에 영향을 안 주는 데이터는 수집하지 않음. "Decision Relevance" 컬럼을 evidence-log 에 추가 |
| **S3** | 모든 답에 "So what?" 한 줄 부착. 답이 또 다른 질문을 낳으면 그 질문도 기록 |
| **S4** | Framework·Question·Method 의 변화를 추적하는 design-log 별도 유지 |
| **S5** | Engagement letter 부합 여부를 매 산출물에 표기 (in-scope / out-of-scope flag) |
| **S6** | 가설 H1, H2... 기록. 각 evidence 가 어느 가설을 지지·반박하는지 attribution |
| **S7** | Cynefin 영역 변화 시 SCOPER 알림. complex 영역이면 probe-sense-respond 사이클 적용 |

### Q16. Method
> **"위 스타일에 맞는 분석 방법 (시장 사이징·경쟁 매핑·시계열·정성 인터뷰 등) 을 합의해 주세요. 사용자께서 이미 알고 있는 방법이 있으면 그것을 차용합니다."**

이 단계에서 **Dual Sizing** (`references/dual-sizing-methodology.md`) 같은 generic 메서드와, **사용자 도메인의 기존 방법** (예: EY 2024 분석 분류 + ad spend 산식) 둘 다 받아냅니다.

### Q17. Validation Approach
> **"답이 틀릴 수 있는 경로는 무엇입니까? 어떻게 검증합니까? smell test / cross-check / dual sizing / triangulation 중 어떤 검증을 적용합니까?"**

Phase A 의 Defensibility 와 Phase C 의 Cross-check 를 종합해 검증 정책을 잠급니다.

### Q18. Risk Identification
> **"본 방법론에서 무엇이 가장 큰 위험입니까? 위험을 어떻게 미리 마킹해 둡니까?"**

자주 나오는 리스크 카테고리:
- 데이터 thinness (특정 국가·세그먼트만 자료 부족)
- 회계연도 변환 오차
- 분류 매핑 충돌 (사용자 분류 vs 외부 표준)
- 외생 변수 영향 (정치·경제·기술)
- 보안·접근 제한 (paywall, login required)

각 리스크에 mitigation 명시 (예: "TH 데이터 부족 → augmentation pass 별도 세션 budget").

### Q19. Resource Constraints
> **"품질 우선입니까, 속도 우선입니까? 세션 분할이 필요할 만큼 큰 작업입니까?"**

Multi-Session Protocol (`references/multi-session-protocol.md`) 트리거 조건:
- IN scope ≥ 6 단위 (예: 카테고리 6 + 국가 2 = 12 단위)
- Defensibility = High
- 외부 데이터 + 내부 데이터 모두 사용
→ 위 조건 충족 시 5–7 세션 분할 권장

---

## 3. Phase D 정리 템플릿

```markdown
## Phase D 정리 (사용자 승인 대기)

### D.1 선택된 리서치 스타일
- **스타일**: [예: S1 + S2 = Issue Decomposition + Decision-Centered]
- **사유**: [한 문장]
- **ANALYST 추가 의무**: [스타일 표에서 그대로 인용]

### D.2 분석 방법
- **시장 사이징**: [Bottom-up + Solution-sum (Dual Sizing)]
- **경쟁 매핑**: [어떻게]
- **외부 프레임워크 차용**: [예: EY 2024 Domain I·II 분류]
- **데이터 수집 채널**: [정부 통계, 산업 리서치, 회사 IR, 협회 발표 등]

### D.3 검증 방식
- **Smell test**: [매 숫자에 적용]
- **Cross-check**: [Phase C.3 의 Bottom-up vs Solution-sum]
- **Dual Sizing 정합**: ±5% 이내 / 초과 시 caveat 의무
- **Source URL 검증**: 200 OK + paywall/login 별도 mark

### D.4 리스크 + Mitigation

| # | 리스크 | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | TH 데이터 thinness | High | High | augmentation pass 세션 budget |
| R2 | FY-CY 변환 오차 | Medium | High | INTEGRATOR audit log |
| R3 | ... | ... | ... | ... |

### D.5 Resource Constraints
- **품질 vs 속도**: [품질 우선 / 속도 우선 / balanced]
- **Multi-Session 트리거**: [yes / no, 사유]
- **예상 세션 수**: [n]

---
**"Phase D 승인" 이라고 답해 주세요.**
```

---

## 4. Phase D 통과 체크

- [ ] Q15 답에 스타일 (S1–S7) 단일 또는 조합 명시
- [ ] Q16 답에 분석 방법 + 외부 프레임워크 차용 명시
- [ ] Q17 답에 검증 정책 명시 (Phase A Defensibility · Phase C Cross-check 와 정합)
- [ ] Q18 답에 리스크 ≥ 3개 + mitigation 명시
- [ ] Q19 답에 multi-session 트리거 여부 명시
- [ ] 사용자 명시 승인

---

## 5. 흔한 함정

| 함정 | 왜 문제 |
|---|---|
| SCOPER 가 사용자에게 묻지 않고 default 스타일 (S1) 적용 | 사용자가 S6 (가설 기반) 가 더 적합한 문제일 때 ANALYST 가 잘못된 데이터 수집 패턴 사용 |
| 검증 방식을 Phase C 와 분리해 잠금 | Defensibility High 인데 검증 약하면 모순. Phase A·C·D 가 정합해야 함 |
| 리스크 식별 후 mitigation 없이 통과 | 리스크가 발생했을 때 ANALYST 가 어떻게 대응할지 미정 |
| Multi-Session 트리거 무시하고 single session 강행 | 토큰 한계로 마지막 phase 누락 위험. 미리 분할이 안전 |

---

## 6. 외부 프레임워크 매핑 (부록 C — 메타데이터)

| 본 가이드 스타일 | 외부 출처 | 비고 |
|---|---|---|
| S1 | McKinsey Issue Tree (Minto/MECE) | 가지별 답 → 종합 결론 |
| S2 | Bain Decision-Centered | priorities first |
| S3 | Booth/Colomb/Williams *Craft of Research* | topic → focused → question → so what |
| S4 | Maxwell *Qualitative Research Design* | interactive components |
| S5 | Generic Consulting Engagement Letter (eForms 등) | contractual scope first |
| S6 | Hypothesis-Driven (Heilmeier Catechism, A/B testing) | falsifiable claims |
| S7 | Cynefin (Snowden) + Wardley Mapping | context-aware analysis |

> 사용자에게는 위 표를 보여주지 않습니다. 회사·인물 이름은 SCOPER 가 알고 있는 메타데이터일 뿐.

---

*Next: `Phase-E-deliverable.md` (산출물·리스크·성공기준)*
