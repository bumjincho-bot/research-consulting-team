---
name: research-consulting-team
description: Country-aware consulting-grade research team — 한국·일본·대만·태국·글로벌 시장에서 컨설팅 수준의 깊이와 검증력을 갖춘 리서치를 수행합니다. 시장 사이징(TAM/SAM/SOM), 경쟁 환경 매핑, 산업·버티컬 분석, 전략 리서치, due diligence, 투자 검토 등 CEO·이사회·투자자에게 제출 가능한 defensible research 가 필요할 때 사용합니다. SCOPER → ANALYST(병렬 3명) → CHECKER A·B(직렬) → INTEGRATOR → ARCHITECT → CRITIC → WRITER → GATEKEEPER → PACKAGER 9단계로 진행하며, 국가별로 공신력 있는 데이터 소스 기준을 다르게 적용하되 최종 산출물은 동일한 methodology, confidence rating, evidence log, 보고서 포맷으로 정렬합니다. 트리거 키워드 - "리서치팀", "심층 리서치", "deep research", "consulting-grade", "defensible", "CEO-ready", "시장 조사", "시장 사이징", "TAM SAM SOM", "경쟁 분석", "경쟁 환경", "산업 분석", "due diligence", "기업 분석", "버티컬 분석", "한국 일본 대만 태국 시장".
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
user_invocable: true
---

# Research Consulting Team — Country-Aware Consulting-Grade Research

> **Distribution**: 팀 내부 전용. Git 커밋 시 `secrets/`, `.env`, `learning-log/runs/` 제외 필수. 외부 배포·오픈소스 공개 금지.

이 스킬은 BCG·McKinsey 같은 컨설팅 펌과 Grand View·Mordor 같은 리서치 하우스의 운영 방식을 본떠, **9개 역할**이 시퀀셜·병렬로 협업하여 신뢰도 높고 방어 가능한 리서치를 만들어냅니다. 한국·일본·대만·태국 등 국가별로 공신력 소스 기준이 달라도 최종 산출물은 같은 형식으로 정렬됩니다.

---

## 언제 사용하나

- 시장 사이징 (TAM/SAM/SOM, 단일 또는 다중 세그먼트·국가)
- 경쟁 환경 매핑 (점유율, 비즈니스 모델, white space)
- 산업·버티컬 분석
- 전략 강화용 evidence 수집
- Due diligence, 투자 검토
- 같은 방법론을 여러 세그먼트·국가에 일관되게 적용해야 할 때
- 최종 산출물이 CEO/이사회/투자자에게 제출되는 경우

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

| 파일 | 용도 |
|---|---|
| `references/source-tiers.md` | S/A/B/C/D/E/F 소스 신뢰도 티어 정의 |
| `references/confidence-rating.md` | High/Medium/Low/Insufficient 부여 기준 |
| `references/tier-mapping.md` | 국가별 소스 → 공통 티어 매핑 규칙 |
| `references/methodology-template.md` | 시장 사이징 방법론 템플릿 |
| `references/report-template.md` | 한국어 최종 보고서 마크다운 포맷 |
| `references/view-spec.md` | 사용자 view/table/slide 요구를 spec 으로 변환 |
| `references/paid-sources-registry.md` | 사용 가능한 유료 사이트 카탈로그 |
| `references/countries/{kr,jp,tw,th,global}.md` | 국가별 공신력 소스 가이드 |
| 🆕 `references/dual-sizing-methodology.md` | **이중 산출** — Bottom-up + Solution 합 병기, ±5% 정합성 검증 |
| 🆕 `references/classification-framework.md` | **이중 분류** — 1차·보조 분류 채택 기준, 미채택 분류 부록 보존 규칙 |
| 🆕 `references/player-notation.md` | **Player 표기** — 회사명·서비스명 컬럼 분리, 매핑 기준, 다국가 적용 |
| 🆕 `references/metrics-standard.md` | **1차 지표 표준** — 솔루션별 맞춤 표현, 보조 가맹점 수, 매출 share 표 형식 |
| 🆕 `references/calculation-log-spec.md` | **산출 로그** — 중간 계산 과정 기록 표준, 계산 체인 추적, CHECKER-A 검증 연동 |
| 🆕 `references/evidence-log-spec.md` | **Evidence Log 표준** — 단일 파일 + status 컬럼 (RAW→VERIFIED/REJECTED), 실시간 append, 서브 에이전트 직접 쓰기 허용 |
| 🆕 `references/multi-session-protocol.md` | **다중 세션 프로토콜** — Large 리서치를 여러 OpenCode 세션으로 분할 운영하는 표준 (session-log.md, NEXT-SESSION-GUIDE.md, CSV 헤더 사전 생성, 잠금 사항 변경 금지 등) |

> **🆕 선택적 적용**: 위 4개 신규 reference 파일의 규칙은 SCOPER 단계에서 **옵션 메뉴** 로 사용자에게 적용 여부를 질문합니다. 방어 강도 High 시 전체 적용 권장, Low 시 선택 가능. 자세한 옵션 메뉴는 `personas/01-scoper.md` 의 "방법론 옵션 메뉴" 참조.

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

### Step 2. SCOPER (Phase 1) — 스코프·방법론·세그먼트 잠금
- `personas/01-scoper.md` 정독
- 리서치 브리프 작성 → **사용자 승인 받기 전까지 다음 단계 금지**
- 사용자가 view/table/slide 요구를 했다면 `references/view-spec.md` 규칙으로 spec 변환
- `references/methodology-template.md` 로 방법론 잠금
- 대상 국가·세그먼트 확정

### Step 3. ANALYST ×3 (Phase 2) — 병렬 조사
- `personas/02-analyst.md` 정독
- 리서처 1/2/3 으로 분야 분할 (예: 1=핵심 영역, 2=시장·경쟁, 3=트렌드·미래)
- 각 리서처는 해당 국가의 `references/countries/{kr|jp|tw|th|global}.md` 먼저 확인
- 유료 소스 사용 시 `references/paid-sources-registry.md` + `policies/credentials-policy.md` 준수
- 모든 데이터 포인트에 **소스 티어 태그** 부착 (S~F)

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

## 빠른 시작 (사용자 입장)

```
사용자: "태국 F&B SaaS 시장 사이징 해줘. CEO 보고용."

1. ORCHESTRATOR: "리서치 의도 확인했습니다. SCOPER 단계로 진입합니다."
2. SCOPER: 브리프 작성 → 사용자 확인
3. ANALYST ×3 병렬 조사 (TH 가이드 + global 가이드 사용)
4. CHECKER A → B 검증
5. INTEGRATOR: TH 단일 국가라 정렬은 단순, confidence rating 부여
6. ARCHITECT: 시장 구조 + so-what
7. CRITIC: weak-point 랭킹
8. WRITER: 한국어 보고서
9. GATEKEEPER: 품질 게이트
10. PACKAGER: 최종 패키지 + learning-log 기록
```

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
