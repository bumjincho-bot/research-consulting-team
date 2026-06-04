# Interview Guide — Domain-Agnostic SCOPER 인터뷰 표준

> **버전**: v2.0 (2026-06-04 신설)
> **호출 시점**: SCOPER (Phase 1) 가 사용자 주제를 받자마자 첫 작업
> **목적**: 산업·도메인 가정 없이, 사용자와 함께 9단계 인터뷰를 거쳐 분류·메트릭·방법론을 **공동 도출**
> **이전 (v1.x)**: SCOPER 가 SaaS 가정 + A~F 옵션 메뉴를 하드코딩 → 다른 도메인에 적용 시 부정확
> **이후 (v2.0)**: SCOPER 가 사용자에게 묻고, 답에 따라 분류·메트릭·방법론을 그 자리에서 합의·기록

---

## 1. 왜 인터뷰인가

`references/_legacy-saas/` 와 `references/_archived-domain-adapter-attempt/ARCHIVED-NOTE.md` 에서 설명한 두 번의 실패 후 도달한 결론:

| 시도 | 문제 |
|---|---|
| v1.x 하드코딩 (FC1-FC6 + 가맹점 메트릭 + A~F 옵션) | SaaS-특화. 광고·핀테크·헬스케어 등에 부정확 |
| v2.0-α 도메인 어댑터 (saas-vertical / digital-advertising / fintech / ...) | "산업"이라는 축 자체가 SaaS 편향의 재발. 리서치는 산업·문제유형·청중·깊이·시간 등 다축 |
| **v2.0 인터뷰 가이드** ✅ | 사용자가 자기 문제를 가장 잘 안다. SCOPER 는 좋은 질문으로 그 답을 끌어내고 합의·기록 |

이 가이드는 **외부 7개 프레임워크의 공통 패턴** 에서 추출됐습니다 (출처는 `references/interview-guide/Phase-D-methodology.md` 끝부록).

---

## 2. 9단계 Generic Scoping Sequence

7개 프레임워크 (MECE/Issue Tree, Decision-Centered, Question-Refinement, Interactive Design, Engagement-Letter, Hypothesis-Driven, Context-First) 가 공통적으로 따르는 순서입니다. 산업·도메인을 전혀 가정하지 않습니다.

```
1. Objective       — 무엇을 결정·설명하려는가
2. Stakeholder     — 누가 이 답을 쓰는가
3. Boundary        — 무엇이 IN / OUT 인가
4. Decomposition   — 어떤 하위 질문으로 쪼개나 (MECE)
5. Evidence        — 어떤 증거가 답을 합당하게 만드는가
6. Method          — 위 증거를 어떻게 모으고 분석하나
7. Risk            — 무엇이 답을 무너뜨릴 수 있는가
8. Success         — 답이 충분한지 어떻게 판정하나
9. Deliverable     — 무엇을, 언제, 누구에게 전달하나
```

5개 Phase 파일이 이 9단계를 묶습니다:

| Phase | 다루는 단계 | 파일 |
|---|---|---|
| A. Objective | 1, 2 | `Phase-A-objective.md` |
| B. Units | 3, 4 | `Phase-B-units.md` |
| C. Metrics | 5 | `Phase-C-metrics.md` |
| D. Methodology | 6, 7 | `Phase-D-methodology.md` |
| E. Deliverable | 8, 9 | `Phase-E-deliverable.md` |

---

## 3. 리서치 스타일 옵션 (Phase D 에서 선택)

회사·기관 이름이 아닌 **방향성**으로 표현합니다. 사용자가 자기 문제에 맞는 스타일을 고르거나 조합합니다.

| 코드 | 스타일 이름 | 한 문장 방향성 | 적합 상황 |
|---|---|---|---|
| **S1** | Issue Decomposition | 큰 질문을 겹치지 않는 5–7 하위 질문으로 쪼개고 가지별 답을 종합 | 시장 사이징, 진입 전략, 다각도 분석 |
| **S2** | Decision-Centered | "이 답이 어떤 결정을 바꾸나?"부터 묻고 그 결정에 필요한 최소 증거만 모음 | M&A, 투자 판단, GO/NO-GO |
| **S3** | Question-Refinement | 막연한 토픽 → 초점 토픽 → 답할 수 있는 질문 → "So what?" → 연구 문제 | 신규 영역, 문제 정의 자체가 미정 |
| **S4** | Interactive Design | Goal·Framework·Question·Method·Validity 동시 설계, 한 요소가 변하면 전체 재조정 | 정성 분석, 조직·문화 리서치 |
| **S5** | Engagement-Letter | Services·Term·Deliverable·Exclusion·Owner·Cost 를 먼저 계약적으로 고정 | 클라이언트 컨설팅, 다자간 협업 |
| **S6** | Hypothesis-Driven | 가설을 먼저 세우고 그것을 지지/반박하는 증거만 수집 | 정책 영향 평가, A/B 검증 |
| **S7** | Context-First | 문제의 맥락(simple·complicated·complex·chaotic)을 먼저 파악, 거기에 맞는 분석 선택 | 도메인 미정, 신규 카테고리 |

스타일은 **단독 또는 조합** 가능합니다 (예: S2 + S6 = "결정 중심 + 가설 기반").

---

## 4. 핵심 원칙

| 원칙 | 의미 |
|---|---|
| **No assumption before question** | 분류·메트릭·방법론은 인터뷰 전에 가정하지 않음. 결과로 도출 |
| **User co-derives** | SCOPER 는 좋은 질문을 던지고, 답을 정리·합의·기록. 사용자가 결정 |
| **Lock after agree** | 합의된 분류·메트릭·방법론은 Phase 2 진입 전 잠금. 이후 변경 시 user re-confirm |
| **Snippet not prescription** | `_legacy-saas/` 같은 과거 패턴은 사용자 문제와 매칭될 때만 SCOPER 가 "예시"로 제시. 강제 적용 금지 |
| **Domain emerges, not assigned** | 산업명·도메인명은 인터뷰 산출물의 메타데이터일 뿐. 인터뷰의 입력값이 아님 |

---

## 5. SCOPER 사용 흐름 (v2.0)

```
[Step 0] 사용자가 주제 제출
   ↓
[Step 1] SCOPER 가 본 README 정독 → Phase A 부터 시작
   ↓
[Step 2] Phase A → B → C → D → E 순차 진행
         각 Phase 종료 시 사용자에게 답 정리 보여주고 명시 승인 받음
   ↓
[Step 3] 5개 Phase 모두 잠긴 후 Research Brief (1쪽) 작성
   ↓
[Step 4] 사용자 최종 승인 → ANALYST 핸드오프
```

각 Phase 파일은 다음을 포함합니다:
- 묻는 질문 (1–5개)
- 좋은 답 / 나쁜 답 예시
- 답을 정리해 보여주는 템플릿
- 다음 Phase 로 넘어가기 전 체크 항목

---

## 6. 산출물 구조 (Research Brief)

5개 Phase 가 끝나면 SCOPER 는 다음 1쪽 문서를 만듭니다 (사용자 명시 승인 대상):

```markdown
## Research Brief — <project name>

### Phase A. Objective
- 핵심 질문: ...
- 의사결정 컨텍스트: ...
- 청중·사용자: ...

### Phase B. Units
- IN scope: ...
- OUT scope: ...
- 분류 체계: ...  ← ← 이게 v1.x 의 "FC1-FC6" 자리
- MECE 분해: ...

### Phase C. Metrics
- 1차 지표: ...  ← ← 이게 v1.x 의 "가맹점 수" 자리
- 단위·시점·기준일: ...
- 증거 기준 (방어 강도): ...

### Phase D. Methodology
- 선택된 리서치 스타일: ...  (S1 / S2 / S6 등)
- 분석 방법: ...
- 데이터 수집 방식: ...
- 검증 방식: ...
- 식별된 리스크: ...

### Phase E. Deliverable
- 산출 형식: ...
- 일정·세션 수: ...
- 성공 판정 기준: ...
- 후속·제외 항목: ...

### Snippet References (있으면)
- 차용한 과거 패턴: ...
- 사유: ...
```

이게 ANALYST·INTEGRATOR·WRITER 가 동적으로 참조할 단일 진실 (single source of truth) 이 됩니다.

---

## 7. recurring-patterns/ (재사용 snippet 보관)

같은 패턴이 여러 리서치에서 반복되면 (예: 디지털 광고 = EY backbone + ad-spend 메트릭) `recurring-patterns/<pattern-name>.md` 에 snippet 으로 보관합니다. 다음 리서치에서 SCOPER 는 인터뷰 중 "이전에 비슷한 패턴이 있었는데 차용하시겠어요?" 라고 **제안만** 하고, 사용자가 결정합니다.

승급 기준: **3회 이상** 같은 패턴이 인터뷰 산출물로 도출됐을 때만 `recurring-patterns/` 에 등록합니다. 사전 등록 금지.

---

*Next: read `Phase-A-objective.md`*
