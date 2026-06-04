# DEPRECATED: classification-framework.md (moved)

> **Status**: MOVED to `references/_legacy-saas/classification-framework.md`
> **Reason**: This file's FC1-FC6 / FN1-FN6 classification was authored exclusively for **offline B2B2C vertical SaaS** (POS / Mobile Order / Booking / CRM / Delivery / Discovery). It does **not** apply to other research domains (digital advertising, fintech, healthcare IT, ecommerce platforms, etc.).
> **v2.0 replacement**: SCOPER (Phase 1) now derives classification through **interview** with the user. See `references/interview-guide/` for the question tree. The legacy SaaS pattern remains available as a **reference snippet** SCOPER may suggest after the user articulates the problem (post-hoc), not before.

---

## How to migrate

| Use case | v2.0 path |
|---|---|
| New research, unknown domain | `references/interview-guide/` (SCOPER will guide you to derive classification) |
| Continuing prior KR/TW/TH SaaS 6-vertical research | `references/_legacy-saas/classification-framework.md` (use as reference snippet only — do NOT enforce on unrelated domains) |
| Cross-skill compatibility (existing reports cite `references/classification-framework.md`) | This stub keeps the path resolvable; redirect to the new location |

---

## Why this was deprecated (lesson learned)

The file embedded SaaS-specific assumptions in a way that made the skill brittle when applied to non-SaaS topics. Specifically: (1) FC1-FC6 names ("POS / 결제", "Booking / 예약" etc.) presupposed offline B2B2C commerce, (2) FN1-FN6 funnel ("Discovery → Retention") presupposed a consumer purchase journey, and (3) the dual-axis taxonomy itself was a SaaS-vertical artifact, not a research methodology.

The fix is to **let SCOPER derive classification with the user** rather than ship a frozen taxonomy. See:
- `references/interview-guide/` — Phase B (Unit of Analysis) walks SCOPER through MECE decomposition with the user
- `references/_archived-domain-adapter-attempt/ARCHIVED-NOTE.md` — explanation of why even "domain adapters" were too prescriptive
