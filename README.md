# research-consulting-team

Country-aware consulting-grade research skill for OpenCode. BCG·McKinsey 급 리서치를 9단계 역할 기반 프로세스로 수행합니다.

## Overview

한국·대만·태국·일본 등 국가별 데이터 소스 기준을 다르게 적용하되, 최종 산출물은 동일한 methodology, confidence rating, evidence log, 보고서 포맷으로 정렬합니다.

## 9-Phase Process

```
ORCHESTRATOR → SCOPER → ANALYST ×3 → CHECKER-A → CHECKER-B
→ INTEGRATOR → ARCHITECT → CRITIC → WRITER → GATEKEEPER → PACKAGER
```

| Phase | Role | Key Responsibility |
|---|---|---|
| 0 | ORCHESTRATOR | 전체 지휘, 단계 전환 관리 |
| 1 | SCOPER | 스코프·방법론·옵션 메뉴 (A~F) 잠금 |
| 2 | ANALYST ×3 | 병렬 조사 (Tier 순서 + Market Landscape Scan) |
| 3a | CHECKER-A | 숫자·단위·시점·smell test |
| 3b | CHECKER-B | 출처·링크·인용 검증 |
| 4 | INTEGRATOR | 국가별 정렬·통화·정합성 검증 |
| 5 | ARCHITECT | Synthesis + so-what + 프레임워크 |
| 6 | CRITIC | CEO 관점 weak-point 랭킹 |
| 7 | WRITER | 보고서 작성 |
| 8 | GATEKEEPER | 맞춤법·논리 게이트 |
| 9 | PACKAGER | Evidence log·CSV·HTML·PDF 패키징 |

## Methodology Options (A~F)

SCOPER 단계에서 사용자에게 선택적 적용 여부를 질문합니다:

| Option | Description | Default (High) |
|---|---|---|
| A | Dual Sizing (Bottom-up + Solution sum, ±5% consistency) | ✅ |
| B | Dual Classification (Solution Rows + F1-F6 Function) | ✅ |
| C | Player Column Separation (Company + Service) | ✅ |
| D | Revenue Share Separate Table | ✅ |
| E | 1st Metric Custom Expression per Solution | ✅ |
| F | Wiki Backbone Integration | ✅ (when wiki exists) |

## Key Features

### Evidence Log (Option A — Single File + Status Column)
- `status`: RAW → VERIFIED / REJECTED / SUPERSEDED
- Real-time append by sub-agents
- CHECKER updates status, WRITER uses VERIFIED only
- History preserved (rejected kept for audit trail)

### Calculation Log
- Every intermediate calculation recorded with formula + inputs + sources
- Enables full chain traceability ("where did this number come from?")

### Market Landscape Scan (ANALYST Step 5)
- Map the whole market landscape BEFORE deep research
- Not just "find new startups" — understand who's big, who's growing, who's entering
- Revenue is not the only size metric: MAU, traffic, merchant count matter
- Growth signals: traffic surge, recent funding, corporate subsidiary entry

### Country-Aware Source Hierarchy
Each country has a dedicated guide (`references/countries/{kr,tw,th,jp,global}.md`) with:
- Tier A government sources ranked by priority
- Listed company filing systems (DART/MOPS/SET)
- Recommended research order
- Common pitfalls (calendar systems, currency, informal economy)

## File Structure

```
research-consulting-team/
├── SKILL.md                          # Entry point (9-phase workflow)
├── README.md                         # This file
├── personas/                         # 11 agent personas (00-09)
├── references/                       # 15 reference files
│   ├── source-tiers.md              # S/A/B/C/D/E/F tier definitions
│   ├── confidence-rating.md         # High/Medium/Low/Insufficient
│   ├── dual-sizing-methodology.md   # Bottom-up + Solution sum
│   ├── classification-framework.md  # Dual classification + rejection rationale
│   ├── player-notation.md           # Company + Service separation rules
│   ├── metrics-standard.md          # 1st metric per solution type
│   ├── evidence-log-spec.md         # Option A: single file + status
│   ├── calculation-log-spec.md      # Computation chain tracking
│   ├── methodology-template.md      # Market sizing template
│   ├── report-template.md           # Report markdown format
│   ├── view-spec.md                 # Table/slide spec conversion
│   ├── tier-mapping.md              # Cross-country source equivalence
│   ├── paid-sources-registry.md     # Licensed source catalog
│   └── countries/                   # Per-country source guides
│       ├── kr.md
│       ├── tw.md
│       ├── th.md
│       ├── jp.md
│       └── global.md
├── policies/                         # 3 security policies
│   ├── credentials-policy.md        # ENV-only, no plaintext
│   ├── paid-source-access.md        # License compliance
│   └── env-loading.md               # .env loading guide
├── secrets/                          # Token storage (git-ignored)
├── learning-log/                     # Run records (git-ignored)
└── .gitignore
```

## Applied In

| Country | Version | Status | Evidence | Tables |
|---|---|---|---|---|
| 🇰🇷 KR | v1.4 | ✅ Complete | 73 entries | 93 |
| 🇹🇼 TW | v2.6 | ✅ Complete | 101 entries | 25 |
| 🇹🇭 TH | v3.5 | 🟡 In Progress | 40 entries | — |

## Security

- No plaintext credentials anywhere (ENV variables only)
- `secrets/.env` git-ignored
- `learning-log/runs/` git-ignored (may contain sensitive research data)
- Citations < 100 words + source attribution mandatory

## Changelog

### v1.6 (2026-05-28)
- Add `references/evidence-log-spec.md` — Option A (single file + status column)
- Add Market Landscape Scan to ANALYST (Step 5)
- Update `personas/02-analyst.md` with growth signal detection + landscape mapping

### v1.5 (2026-05-27)
- Initial GitHub release
- 11 personas + 15 references + 3 policies + 5 country guides
- Methodology options A~F (selective application at SCOPER stage)
- Calculation log spec for computation chain tracing

## License

Internal use only. Do not distribute externally or open-source.
