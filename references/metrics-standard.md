# DEPRECATED: metrics-standard.md (moved)

> **Status**: MOVED to `references/_legacy-saas/metrics-standard.md`
> **Reason**: This file's "1차 지표" standard ("가맹점 수", "도입 호텔 수", "사용 의원 수", "활성 매장 수") presupposes SaaS-vertical operating-leverage analysis. It does **not** translate to digital advertising (ad spend / impressions / reach), fintech (transaction volume / take rate), policy research, academic surveys, or other non-SaaS topics.
> **v2.0 replacement**: SCOPER (Phase 1) now derives metrics through **interview** in Phase C (Metric Derivation). See `references/interview-guide/`.

---

## How to migrate

| Use case | v2.0 path |
|---|---|
| New research, unknown metric | `references/interview-guide/` Phase C — SCOPER asks user what number/indicator best supports the decision |
| Continuing prior KR/TW/TH SaaS 6-vertical research | `references/_legacy-saas/metrics-standard.md` (legacy reference; do NOT impose 가맹점-style framing on unrelated domains) |

---

## Why this was deprecated

"가맹점 수 / GMV / 활성 매장" is a vocabulary set that makes sense in offline B2B2C SaaS where merchants pay subscription fees to operate storefronts. In other research contexts:

- Digital advertising → metric is **ad spend (USD M)**, **CPM**, **CPC**, **share-of-spend**, **reach × frequency**
- Fintech → **transaction volume (USD B GMV)** × **take rate (bps)**
- Healthcare IT → **registered clinics / hospitals / patients seen / EMR sessions**
- Policy / academic research → **policy adoption rate / population coverage / treatment effect size**

Forcing 가맹점 vocabulary on these domains creates downstream confusion. The fix: SCOPER asks the user what metric best supports the decision, then locks it.
