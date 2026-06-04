# Legacy SaaS References (v1.x archived)

> **Status**: ARCHIVED — these files defined the **SaaS-vertical** specialization of the skill. They remain available as historical reference + reusable snippets, but are **not loaded by default** in v2.0+.
> **Replaced by**: `references/interview-guide/` (interview-driven SCOPER)

---

## What's in this folder

| File | Original purpose | Why deprecated | Reusable as |
|---|---|---|---|
| `classification-framework.md` | FC1-FC6 + FN1-FN6 dual-axis taxonomy for offline B2B2C SaaS | Embedded SaaS commerce vocabulary (POS / Booking / Delivery) as universal | Reference snippet for vertical-SaaS researches |
| `metrics-standard.md` | "가맹점 수 / GMV / 활성 매장" 1차 지표 standard | Vocabulary doesn't generalize beyond SaaS subscription unit economics | Reference snippet when user explicitly chooses 가맹점-style framing |
| `calculation-log-spec.md` | Calculation-log columns + ARPU × 가맹점 examples | General discipline (log every estimate) → moved to interview Phase D; SaaS templates remain here | Template snippet for SaaS calculation logs |
| `player-notation.md` | 회사명 ↔ 서비스명 2-column player table | 2-column structure is SaaS-vertical specific (advertising needs 3, fintech needs other) | Reference snippet for SaaS-vertical researches |

---

## When to use these (post-hoc only)

After SCOPER (v2.0+) interviews the user and the user articulates the problem, SCOPER may **suggest** one of these snippets if the user's chosen methodology matches the legacy pattern. The suggestion sounds like:

> "Your problem looks similar to the prior KR/TW/TH 6-vertical SaaS research. They used the FC1-FC6 / FN1-FN6 taxonomy from `_legacy-saas/classification-framework.md`. Would you like to adopt that taxonomy as a starting point, or design a new one?"

The user (not SCOPER) decides. Default is "design a new one with my help".

---

## What survived from v1.x into v2.0 core

These principles **were** generalizable and were promoted out of `_legacy-saas/` into the core skill:

| Principle | v2.0 location |
|---|---|
| Dual sizing (Bottom-up + Solution sum, ±5% reconciliation) | `references/dual-sizing-methodology.md` (kept in core) |
| Evidence log discipline (RAW → VERIFIED → REJECTED → SUPERSEDED) | `references/evidence-log-spec.md` (kept in core; SaaS examples removed) |
| Source tier criteria (S/A/B/C/D/E) | `references/source-tiers.md` (kept; methodology-agnostic) |
| Confidence rating | `references/confidence-rating.md` (kept) |
| Multi-session protocol | `references/multi-session-protocol.md` (kept) |
| Wiki snapshot policy | `references/wiki-snapshot-policy.md` (kept; methodology-agnostic) |
| View spec | `references/view-spec.md` (kept) |
| Methodology template | `references/methodology-template.md` (kept; example-only updates) |

---

## Migration timeline

- **2026-06-04**: Files moved to `_legacy-saas/`. Redirect stubs left at original paths so existing reports' links don't break.
- **No deletion planned** — these files remain available indefinitely for reference.
