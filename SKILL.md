---
name: research-consulting-team
description: Domain-agnostic consulting-grade research team — 어떤 주제든 사용자와 인터뷰로 분류·메트릭·방법론을 공동 도출한 뒤, 9-Phase 워크플로우로 신뢰도 높은 리서치를 산출합니다. 시장 사이징·경쟁 매핑·산업 분석·due diligence·정책 영향·정성 인터뷰 등 형태에 무관하게 사용. SCOPER (interview-driven Phase A~E) → ANALYST(병렬 3명) → CHECKER A·B → INTEGRATOR → ARCHITECT → CRITIC → WRITER → GATEKEEPER → PACKAGER. 분류·메트릭·방법론은 모두 사용자 인터뷰 산출물 (skill 이 사전 가정 X). v2.0 부터 SaaS-편향 제거 + 인터뷰 가이드 도입. 트리거 키워드 - "리서치팀", "심층 리서치", "deep research", "consulting-grade", "defensible", "CEO-ready", "시장 조사", "시장 사이징", "TAM SAM SOM", "경쟁 분석", "산업 분석", "due diligence", "정책 분석", "정성 리서치", "가설 검증".
triggers:
  - "리서치팀"
  - "심층 리서치"
  - "deep research"
  - "consulting-grade"
  - "defensible 리서치"
  - "CEO-ready"
  - "시장 조사"
  - "시장 사이징"
  - "TAM SAM SOM"
  - "경쟁 분석"
  - "경쟁 환경"
  - "산업 분석"
  - "due diligence"
  - "기업 분석"
  - "정책 분석"
  - "정성 리서치"
  - "가설 검증"
  - "evidence-based research"
user_invocable: true
---

# Research Consulting Team — Domain-Agnostic Consulting-Grade Research

> **Distribution**: 팀 내부 전용. Git 커밋 시 `secrets/`, `.env`, `learning-log/runs/` 제외 필수. 외부 배포·오픈소스 공개 금지.
> **Version**: v2.0 (2026-06-04 — interview-driven scoping)

이 스킬은 BCG·McKinsey 같은 컨설팅 펌과 학술 리서치 방법론의 운영 방식을 본떠, **9개 역할**이 시퀀셜·병렬로 협업하여 신뢰도 높고 방어 가능한 리서치를 만들어냅니다. **v2.0 부터 도메인·산업 가정 없이** 사용자와 SCOPER 인터뷰를 통해 분류·메트릭·방법론을 공동 도출합니다.

---

## 언제 사용하나

- 시장 사이징 (TAM/SAM/SOM, 단일 또는 다중 세그먼트·국가)
- 경쟁 환경 매핑 (점유율, 비즈니스 모델, white space)
- 산업·버티컬 분석
- 디지털 광고·핀테크·헬스케어 등 **임의 도메인** 시장 분석
- 정책 영향 평가 / 가설 검증 / 시계열 분석
- 정성 인터뷰 기반 리서치
- 전략 강화용 evidence 수집
- Due diligence, 투자 검토
- 같은 방법론을 여러 세그먼트·국가에 일관되게 적용해야 할 때
- 최종 산출물이 CEO·이사회·투자자·정책결정자에게 제출되는 경우

---

## 9개 역할 (한 사람이 마음가짐을 바꿔가며 모두 수행)

```
┌──────────────────┐
│ 0. ORCHESTRATOR  │  전체 지휘, 단계 전환 관리, 사용자 커뮤니케이션
└────────┬─────────┘
         │
┌────────▼─────────┐    ┌──────────────────┐
│   1. SCOPER      │───▶│  2. ANALYST ×3   │  병렬 조사 (담당 분야 분할)
│  (Engagement     │    │  (Researchers)   │
│    Partner)      │    └────────┬─────────┘
└──────────────────┘             │
                                 ▼
                        ┌──────────────────┐
                        │ 3a. CHECKER-A    │  숫자·단위·시점·smell test
                        │   (Numbers)      │
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 3b. CHECKER-B    │  출처·링크·인용·기관 검증
                        │   (Sources)      │
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 4. INTEGRATOR    │  ⭐ 국가별 차이 정렬·통화 통일·갭 보완
                        │ (Country-Aware)  │     confidence rating 부여
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 5. ARCHITECT     │  synthesis + so-what + 프레임워크
                        │ (Sr. Consultant) │
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 6. CRITIC        │  CEO 관점 weak-point 랭킹
                        │ (Partner Review) │
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 7. WRITER        │  한국어 보고서 작성 (기승전결)
                        │ (구성작가)        │
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 8. GATEKEEPER    │  맞춤법·문장·논리 게이트
                        │ (게이트키퍼)       │
                        └────────┬─────────┘
                                 │
                                 ▼
                        ┌──────────────────┐
                        │ 9. PACKAGER      │  evidence log·methodology·assumptions
                        │ (Delivery)       │
                        └──────────────────┘
```

각 단계 진입 시 해당 페르소나 파일을 읽고 **mindset 을 명시적으로 전환**합니다.

| Phase | Persona | 파일 |
|---|---|---|
| 0 | ORCHESTRATOR (총괄) | `personas/00-orchestrator.md` |
| 1 | SCOPER (Engagement Partner) | `personas/01-scoper.md` |
| 2 | ANALYST ×3 (Researchers) | `personas/02-analyst.md` |
| 3a | CHECKER-A (숫자) | `personas/03a-checker-numbers.md` |
| 3b | CHECKER-B (출처) | `personas/03b-checker-sources.md` |
| 4 | INTEGRATOR (국가별 정렬) | `personas/04-integrator.md` |
| 5 | ARCHITECT (Senior Consultant) | `personas/05-architect.md` |
| 6 | CRITIC (Partner Review) | `personas/06-critic.md` |
| 7 | WRITER (구성작가) | `personas/07-writer.md` |
| 8 | GATEKEEPER (품질 관리) | `personas/08-gatekeeper.md` |
| 9 | PACKAGER (Delivery) | `personas/09-packager.md` |

---

## 핵심 공통 자료 (모든 페르소나가 참조)

### v2.0 핵심 (Interview-Driven Scoping)

| 파일 | 용도 |
|---|---|
| 🆕 `references/interview-guide/README.md` | **9-step generic sequence + 7 리서치 스타일 개요** (Phase A~E 통합) |
| 🆕 `references/interview-guide/Phase-A-objective.md` | 목적·의사결정·청중 잠금 (Q1~Q5) |
| 🆕 `references/interview-guide/Phase-B-units.md` | 스코프·분류·MECE 분해 (Q6~Q9) |
| 🆕 `references/interview-guide/Phase-C-metrics.md` | 1차 지표·단위·증거 기준 (Q10~Q14) |
| 🆕 `references/interview-guide/Phase-D-methodology.md` | **7개 리서치 스타일 + 방법론 합의** (Q15~Q19) |
| 🆕 `references/interview-guide/Phase-E-deliverable.md` | 산출물·일정·성공기준·후속 (Q20~Q24) |
| 🆕 `references/interview-guide/recurring-patterns/` | 사후 추출 snippet 보관소 (3회 이상 반복 시 등록) |

### Domain-Agnostic 공통 자료

| 파일 | 용도 |
|---|---|
| `references/source-tiers.md` | S/A/B/C/D/E/F 소스 신뢰도 티어 정의 |
| `references/confidence-rating.md` | High/Medium/Low/Insufficient 부여 기준 |
| `references/tier-mapping.md` | 국가별 소스 → 공통 티어 매핑 규칙 |
| `references/methodology-template.md` | 시장 사이징 방법론 템플릿 (Phase D 에서 차용 가능) |
| `references/report-template.md` | 한국어 최종 보고서 마크다운 포맷 |
| `references/view-spec.md` | 사용자 view/table/slide 요구를 spec 으로 변환 |
| `references/paid-sources-registry.md` | 사용 가능한 유료 사이트 카탈로그 |
| `references/countries/{kr,jp,tw,th,global}.md` | 국가별 공신력 소스 가이드 |
| `references/dual-sizing-methodology.md` | Bottom-up + Solution 합 산식 (Phase C·D 에서 차용 가능) |
| `references/evidence-log-spec.md` | Evidence Log 공통 컬럼 + status 컬럼 표준 (도메인-agnostic 컬럼은 SCOPER 가 Brief 에서 추가) |
| `references/multi-session-protocol.md` | Large 리서치 세션 분할 표준 |
| `references/wiki-snapshot-policy.md` | (해당 시) 외부 Wiki backbone 차용 시 snapshot 의무 |

### Archived (v1.x 잔재 — v2.0 에서는 인용 금지, 사용자 명시 차용 시에만 snippet 으로)

| 파일 | 상태 |
|---|---|
| `references/_legacy-saas/classification-framework.md` | FC/FN 이중축 (SaaS-편향) |
| `references/_legacy-saas/metrics-standard.md` | 가맹점/GMV (SaaS-편향) |
| `references/_legacy-saas/calculation-log-spec.md` | ARPU × 가맹점 예제 (SaaS-편향) |
| `references/_legacy-saas/player-notation.md` | 회사·서비스 2-컬럼 (SaaS-편향) |
| `references/_archived-domain-adapter-attempt/` | v2.0-α 도메인 어댑터 시도 (실패 사유 기록) |

> **v2.0 원칙**: 분류·메트릭·방법론은 SCOPER 인터뷰 산출물에서 도출. Skill 이 사전 가정하지 않음. 위 archive 자료는 사용자가 인터뷰 중 명시적으로 차용 결정한 경우에만 snippet 으로 참조.

---

## 보안·자격증명 정책 (사용 전 필수 숙지)

| 파일 | 용도 |
|---|---|
| `policies/credentials-policy.md` | ENV 만 참조, 평문 노출 금지, 마스킹 규칙 |
| `policies/paid-source-access.md` | 유료 소스 합법·안전 접근 규칙, 라이선스 |
| `policies/env-loading.md` | `.env` 로딩 방법, OS별 가이드 |
| `secrets/README.md` | 자격증명 보관소 사용법 (이 폴더는 git 차단) |
| `.env.example` | 자격증명 템플릿 (실제 값은 `secrets/.env` 에) |

**핵심 규칙 (위반 시 즉시 사고)**:
1. ID/PW/API key 의 **실제 값**은 `secrets/.env` 에만 둔다. 다른 어떤 파일에도 평문 작성 금지.
2. 페르소나·로그·보고서·learning-log 에는 **ENV 변수 이름만** 참조 (예: `STATISTA_API_KEY` 사용).
3. 출력에 자격증명이 노출돼야 한다면 마스킹 (예: `sk-***...***ab12`).
4. 멤버 퇴장 또는 유출 의심 시 즉시 로테이션.

---

## Learning Log

같은 리서치를 반복할수록 품질이 좋아지도록, 각 실행의 핵심 산출물·방법론·실패 케이스를 `learning-log/runs/` 에 남깁니다.

- `learning-log/README.md` — 사용법
- `learning-log/runs/{YYYY-MM-DD-topic}/` — 개별 실행 기록 (Git 차단)

다음 리서치 시작 시 ORCHESTRATOR 가 비슷한 주제의 과거 run 을 먼저 검색합니다.

---

## 워크플로우 실행 순서

사용자가 이 스킬을 트리거하면 **ORCHESTRATOR 마인드셋**으로 진입합니다. 절대 곧바로 데이터 수집부터 시작하지 않습니다.

### Step 1. ORCHESTRATOR 진입
- `personas/00-orchestrator.md` 정독
- 사용자 요청을 받아 SCOPER 단계로 안내

### Step 2. SCOPER (Phase 1) — Interview-Driven Scoping (v2.0)
- `personas/01-scoper.md` 정독 (v2.0)
- `references/interview-guide/` 의 README + Phase A~E 정독
- 사용자와 인터뷰: Phase A (목적) → B (단위·분류) → C (메트릭) → D (스타일·방법론) → E (산출물·성공기준)
- 각 Phase 마다 사용자에게 **명시 승인** 받음 ("Phase A 승인" 등)
- 5개 Phase 모두 잠긴 후 통합 Research Brief (1쪽) 작성 → **사용자 최종 승인 받기 전까지 ANALYST 진입 금지**
- 분류·메트릭·방법론은 모두 사용자 인터뷰 산출물 (skill 이 사전 가정 X)
- 사용자가 view/table/slide 요구를 했다면 `references/view-spec.md` 규칙으로 spec 변환 (Phase E 내부)

### Step 3. ANALYST ×3 (Phase 2) — Research Brief 동적 참조 (v2.0)
- `personas/02-analyst.md` 정독 (v2.0)
- SCOPER 가 produced 한 Research Brief 정독 (single source of truth)
- 분야 분할은 Brief 의 Q8·Q9 segment map 기반 (도메인 가정 금지)
- 각 리서처는 해당 국가의 `references/countries/{kr|jp|tw|th|global}.md` 먼저 확인
- 유료 소스 사용 시 `references/paid-sources-registry.md` + `policies/credentials-policy.md` 준수
- 모든 데이터 포인트에 **소스 티어 태그** 부착 (S~F) + Brief Phase D 스타일별 의무 (S1~S7) 충족

### Step 4. CHECKER-A → CHECKER-B (Phase 3) — 직렬 검증
- `personas/03a-checker-numbers.md` → 숫자·단위·시점·smell test
- `personas/03b-checker-sources.md` → 출처·링크·인용·기관 검증
- 둘 다 통과한 데이터만 다음 단계로

### Step 5. INTEGRATOR (Phase 4) — 국가별 정렬
- `personas/04-integrator.md` 정독
- 국가별 통화·기준일·소스 티어를 공통 기준으로 정렬
- `references/tier-mapping.md` 로 국가 간 소스 동등성 확인
- 갭이 있는 국가는 명시적으로 "Insufficient" 라벨 + 보완 액션
- 세그먼트별 confidence rating 확정 (`references/confidence-rating.md`)

### Step 6. ARCHITECT (Phase 5) — synthesis
- `personas/05-architect.md` 정독
- 검증된 데이터로 프레임워크·매트릭스 구성
- 각 세그먼트마다 **"so what?" 한 문장** 필수

### Step 7. CRITIC (Phase 6) — CEO 관점 검증
- `personas/06-critic.md` 정독
- 모든 숫자·결론을 "내가 CEO 라면 어디를 공격할까" 관점으로 점검
- Tier 1(Fragile) 항목은 강화·caveat·제거 중 하나로 처리

### Step 8. WRITER (Phase 7) — 한국어 보고서
- `personas/07-writer.md` 정독
- `references/report-template.md` 형식으로 한국어 보고서 작성
- 사용자가 view spec 을 줬다면 그 틀에 맞게 정렬

### Step 9. GATEKEEPER (Phase 8) — 마지막 게이트
- `personas/08-gatekeeper.md` 정독
- 맞춤법·띄어쓰기·문장 호응·논리 정합성 점검
- 한 번 더 팩트 교차 검증

### Step 10. PACKAGER (Phase 9) — 산출물 정리
- `personas/09-packager.md` 정독
- evidence log, methodology page, assumptions-to-validate, 보고서 본문 동시 제출
- learning-log/runs/ 에 핵심 기록 저장

### Step 11. ORCHESTRATOR 최종 검토 후 사용자 전달

각 단계 전환 시 **"○○ 단계로 넘어갑니다 — 이유: ..."** 한 줄로 사용자에게 알립니다. 투명성이 신뢰를 만듭니다.

---

## 프로젝트 규모별 적용

| 규모 | 세그먼트 수 | 국가 수 | 단계별 깊이 | 권장 세션 구조 |
|---|---|---|---|---|
| Small | 1-2 | 1 | 정상 | 단일 세션 |
| Medium | 3-5 | 1-2 | 정상 | 2-3 세션 (`references/multi-session-protocol.md` 패턴 1) |
| Large | 6+ | 3+ | 우선순위 차등 | 다중 세션 (`references/multi-session-protocol.md` 패턴 2 또는 3) |

Large 의 경우, ORCHESTRATOR 가 우선순위 세그먼트만 풀 깊이로 처리하고 나머지는 lighter treatment 로 표기하는 옵션을 제안합니다.

> **다중 세션 자동 적용 조건**: 세그먼트 ≥ 6, 국가 ≥ 3, 방어 강도 = High, 옵션 3개+ 동시 적용, 또는 ANALYST 예상 evidence-log 행 ≥ 200 중 **하나라도** 해당 시 다중 세션 패턴 적용 권장. SCOPER 단계에서 사용자에게 명시적으로 알릴 것 (`references/multi-session-protocol.md` § 1, § 11.1).

---

## 산출물 체크리스트 (PACKAGER 가 검증)

- [ ] 메인 보고서 (한국어, `report-template.md` 형식)
- [ ] Evidence log (모든 데이터 포인트의 소스·티어·URL·날짜·라이선스 노트)
- [ ] Methodology page (재현 가능한 계산식·가정·환율·기준일)
- [ ] Assumptions-to-validate (외부 발표 전 검증 필요 항목)
- [ ] Confidence rating per 세그먼트 per 국가
- [ ] Weak points list (CRITIC 출력)
- [ ] (옵션) 프레젠테이션 스크립트
- [ ] learning-log entry (다음 실행 시 참조)

모든 숫자가 출처 또는 문서화된 공식으로 추적 가능해야 합니다. 그렇지 않으면 PACKAGER 가 반려합니다.

---

## 빠른 시작 (사용자 입장 — v2.0)

```
사용자: "TW·TH 디지털 광고 시장 사이징 + LINE 포지션. CEO 보고용."

1. ORCHESTRATOR: "리서치 의도 확인했습니다. SCOPER 인터뷰로 진입합니다."
2. SCOPER (Phase A): 목적·청중·방어강도 인터뷰 → 사용자 "Phase A 승인"
3. SCOPER (Phase B): 분류 차원 (사용자가 EY Domain I·II 차용) → "Phase B 승인"
4. SCOPER (Phase C): 메트릭 (ad spend USD M, FY 단위) → "Phase C 승인"
5. SCOPER (Phase D): 스타일 (S1 Issue Decomposition) + 방법론 → "Phase D 승인"
6. SCOPER (Phase E): MD/HTML/PDF + Multi-Session 5–7 → "Phase E 승인"
7. SCOPER: 통합 Research Brief 1쪽 → 최종 승인
8. ANALYST ×3: Brief 의 Segment Map 기반 병렬 조사 (Brief 의 분류·메트릭 그대로)
9. CHECKER A → B 검증
10. INTEGRATOR: FY-CY 변환·통화 환산·confidence rating
11. ARCHITECT: 시장 구조 + so-what
12. CRITIC: weak-point 랭킹 (Brief Phase D 스타일별 의무 충족 여부 점검)
13. WRITER: 한국어 또는 영어 보고서 (Brief Phase E 의 산출 형식)
14. GATEKEEPER: 품질 게이트 (Brief Phase E.A1~An acceptance criteria)
15. PACKAGER: 최종 패키지 + learning-log 기록
```

> **v1.x 와 다른 점**: 분류 (FC1-FC6 등) 와 메트릭 (가맹점 수 등) 을 skill 이 미리 가정하지 않습니다. 인터뷰에서 사용자가 직접 도출합니다.

---

---

## Skill Version History

| Version | Date | Changes |
|---|---|---|
| v1.5 | 2026-05-28 | Initial commit (39 files): 9-phase process, 5 country guides, dual sizing, evidence-log spec, classification framework |
| v1.6 | 2026-05-28 | Added Market Landscape Scan (ANALYST Step 5) + Evidence Log Spec Option A (status column) |
| v1.7 | 2026-05-30 | **Multi-session protocol** + CHECKER/WRITER evidence-log alignment (3 session-split patterns, RAW→VERIFIED chain enforcement) |
| v1.8 | 2026-05-29 | **Wiki v10 alignment**: Classification framework split (Funnel FN1-FN6 ≠ Function FC1-FC6); Wiki snapshot policy (mandatory); Function metric grading (실측/추정/산출 불가); KR/TW/TH report relabeling guide |
| **v2.0** | **2026-06-04** | **Domain-agnostic + interview-driven scoping**. SCOPER 가 사용자와 5 Phase 인터뷰로 분류·메트릭·방법론 도출. SaaS-편향 references → `_legacy-saas/`. 도메인 어댑터 시도 → `_archived-domain-adapter-attempt/`. 새 source of truth: `references/interview-guide/`. ANALYST·SCOPER persona 전면 리팩터. |

### v2.0 Critical Changes (2026-06-04)

After applying the skill to non-SaaS research (digital advertising, FY26 forecast) revealed that v1.x SaaS assumptions (FC1-FC6, 가맹점 metrics, A~F option menu) did not generalize, and an intermediate "domain adapter" attempt itself reproduced the same bias by treating "industry" as the dominant axis — the skill was refactored:

1. **Interview-driven scoping** — SCOPER no longer presents a hardcoded option menu. Instead it conducts a 5 Phase Socratic interview (Phase A objective → B units → C metrics → D methodology → E deliverable) where the user co-derives classification, metrics, and methodology. See `references/interview-guide/`.
2. **7 research styles** — Phase D presents 7 generic research styles (Issue Decomposition / Decision-Centered / Question-Refinement / Interactive Design / Engagement-Letter / Hypothesis-Driven / Context-First) **without** company or institution names. User picks one or combines.
3. **SaaS legacy preserved** — FC/FN classification, 가맹점 metrics, etc. moved to `references/_legacy-saas/` with redirect stubs at original paths (existing reports' links remain valid). These remain available as **post-hoc snippets** SCOPER may suggest after the user articulates the problem, never as a precondition.
4. **Domain adapter rejected** — An intermediate v2.0-α attempt to pre-define adapters per industry (saas-vertical, digital-advertising, fintech, ...) was archived to `references/_archived-domain-adapter-attempt/` because the "industry" categorization itself reproduced the same bias.
5. **Recurring patterns post-hoc** — `references/interview-guide/recurring-patterns/` starts empty. Patterns are promoted only after **3+ independent runs** produce the same combination through interview, not before.
6. **SCOPER + ANALYST personas v2.0** — Both personas refactored. Old versions backed up to `personas/01-scoper.v1.bak.md` and `personas/02-analyst.v1.bak.md`.

### v2.0 Migration Notes

- **Existing v1.8 reports** (KR/TW/TH 6-vertical SaaS): unaffected. Original `references/classification-framework.md` etc. paths still resolve via redirect stubs to `_legacy-saas/`.
- **New researches**: SCOPER will conduct 5 Phase interview. Users may explicitly choose to borrow legacy SaaS patterns when offered as snippets, but no longer by default.
- **Personas 3a/3b/4–9**: not yet refactored in v2.0. They reference SCOPER's Research Brief (single source of truth) but still contain some v1.x phrasing. Refactor planned for v2.1.

---

## 참고 — 두 원본 스킬과의 관계

이 스킬은 두 원본 스킬을 합성·확장한 별도 산출물입니다. 원본은 변경하지 않습니다.

- **Deep Research** (영어, 6단계 시퀀셜): SCOPER·ANALYST·CHECKER·ARCHITECT·CRITIC·PACKAGER 골격 흡수
- **Research Team** (한국어, 8명 협업): 병렬 리서처·팩트체커 A/B 분리·구성작가·게이트키퍼 흡수

추가된 것:
- **INTEGRATOR** (Phase 4): 국가별 소스 차이를 공통 기준으로 정렬
- **Country-aware source layer**: KR/JP/TW/TH/Global 별 공신력 소스 가이드
- **View spec 변환**: 사용자가 원하는 표·슬라이드 구조에 맞춰 조사
- **Learning log**: 반복 실행 시 품질 누적
- **Credentials policy**: ENV-only 자격증명 관리 + secrets/ 폴더 + .gitignore 이중 차단
