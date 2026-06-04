# ⚠️ Archived: Domain Adapter Attempt (2026-06-04)

> **Status**: ARCHIVED — not used in production. See reason below.
> **Authored by**: Sisyphus (Prometheus session continuation)
> **Replaced by**: `references/interview-guide/` (interview-driven scoping)

---

## Why this approach was archived

This folder represents an early attempt to solve the **SaaS-bias** problem in the skill (originally framed as: how do we apply this skill to non-SaaS research, e.g. digital advertising?).

The attempted solution was: pre-define **domain adapters** (saas-vertical, digital-advertising, fintech, healthcare-it, ...) and have SCOPER match the user's topic to a domain via trigger keywords, then load the corresponding classification / metrics / methodology files.

**The user's meta-critique that retired this approach** (paraphrased):

> "도메인이라고 하는게 맞는지 잘 모르겠다. 리서치라는게 범위가 워낙 넓다보니까 문답 형식으로 주제를 찾아가야하지 않을까?"

The user was right. The "domain" categorization itself reproduces the same SaaS-bias failure mode: it pre-supposes that **industry** is the dominant axis on which research splits. But research topics vary along many axes (question type, defensibility bar, audience, depth, time horizon, data availability), and "industry" is only one. Pre-defined domain adapters smuggle in classification / metric / methodology assumptions before the user even articulates the problem.

The replacement is an **interview-driven SCOPER**: the SCOPER asks Socratic questions and the user co-derives classification, metrics, and methodology together. Reference snippets (which include the artifacts in this archive) become **post-hoc** patterns the SCOPER can suggest **after** the user articulates the problem — not pre-conditions.

---

## What was here (preserved for reference)

- `README.md` — domain adapter contract (4-file interface: README + classification + metrics + methodology-options)
- `_domain-detection-guide.md` — trigger-keyword routing logic (still useful as **inspiration** for the Phase A interview questions: industry-pattern recognition can be one of many cues)
- `_generic/` (empty) — was meant as fallback adapter
- `saas-vertical/` (empty) — was meant to host the migration of FC/FN classification + 가맹점/GMV metrics
- `digital-advertising/` (empty) — was meant to host EY Domain I·II + ad-spend metrics

---

## What survived into the new design

| Idea | Outcome |
|---|---|
| 4-file interface (README + classification + metrics + methodology) | Repurposed as **interview output template** — SCOPER + user fill these together, not load pre-built |
| `_generic` fallback | Replaced by **interview is always required** — there is no fallback to skip it |
| Trigger keyword matching | Demoted to a **cue** SCOPER can use during Phase A, not a routing decision |
| Adapter-vs-skill separation | Preserved in the form of: skill = workflow / interview-guide = method-derivation / `_legacy-saas/` = past-pattern snippets |

---

## When to revisit

If after 5+ research engagements run through the new interview-driven SCOPER, certain combinations recur (e.g. 3+ digital-ad researches all converge on EY-style classification + ad-spend metrics), it may then be worth promoting that recurring combination to a **named pattern** in `interview-guide/recurring-patterns/`. That promotion happens **after** observed repetition, not before.

This archive remains for that retrospective.
