# Interaction Protocol — Sisyphus Runtime, Skill Contract

`research-consulting-team` 에서 Sisyphus 는 runtime orchestrator 입니다. Skill 의 ORCHESTRATOR persona 는 workflow contract owner 입니다. Sisyphus 는 persona 일을 직접 대신하지 않고, contract 를 sub-agent prompt 에 삽입하고 결과를 gate 로 판정합니다.

## Execution Loop

```text
User request
  -> Sisyphus loads SKILL.md and personas/00-orchestrator.md
  -> Sisyphus selects next persona and reads that persona file
  -> Sisyphus builds sub-agent prompt with required contract bundle
  -> sub-agent executes one persona role only
  -> sub-agent ends with SISYPHUS_HANDOFF_ENVELOPE
  -> Sisyphus checks GATE_RESULT and gate IDs
  -> PASS: advance to next persona
  -> FAIL/PARTIAL: repair, reroute, or ask user
```

## Pre-Flight Bundle

Before delegating a persona phase, Sisyphus includes these items in the sub-agent prompt.

1. Target persona file content or exact path, e.g. `personas/02-analyst.md`.
2. `references/role-contracts/SCHEMA.md`.
3. This interaction protocol.
4. Prior phase envelope, if one exists.
5. Active Research Brief for phases 2 and later.
6. Relevant reference files named by the persona, such as source tiers, confidence rating, evidence log spec, or view spec.

If any required item is missing, Sisyphus does not start the phase. It returns to the producing persona or asks the user.

## Delegation Prompt Requirements

Every Sisyphus delegation prompt under this skill must contain these sections.

- `ROLE CONTRACT`: target persona identity, scope, inputs, outputs, gates, and forbidden actions.
- `INPUTS`: exact artifacts passed from prior phase.
- `TASK`: the one phase-specific action to perform.
- `EXPECTED OUTCOME`: concrete artifacts and envelope requirement.
- `MUST NOT DO`: no scope drift, no hidden assumptions, no credential exposure, no unsupported evidence.
- `HANDOFF`: instruction to end with `SISYPHUS_HANDOFF_ENVELOPE` and one `GATE_RESULT:` token.

## Sisyphus Verification

After a sub-agent returns, Sisyphus checks in this order.

1. Envelope exists and is the final block.
2. Exactly one `GATE_RESULT:` token exists.
3. All persona-required `INPUT_*`, `OUTPUT_*`, and `GATE_*` IDs are mentioned.
4. `GATE_RESULT: PASS` has no material failures.
5. `GATE_RESULT: FAIL` or `PARTIAL` includes repair target and reason.
6. Security and credential policy are not violated.

## Repair Loop

- Same-persona repair is allowed up to 2 times when the failure is local.
- Upstream rollback is required for `MISSING_INPUT`, `BRIEF_DRIFT`, `NUMBER_FAILURE`, or `SOURCE_FAILURE` when the producing phase owns the issue.
- Immediate stop is required for `SECURITY_VIOLATION`.
- If 2 repair attempts fail, Sisyphus returns to ORCHESTRATOR persona and reports the blocker to the user.

## Cross-Phase Contamination

If a downstream phase detects upstream contamination, Sisyphus must not patch the artifact silently. It sends a `REPAIR_REQUEST` to the persona that owns the artifact. Examples:

- CHECKER_A finds unit mismatch in ANALYST rows -> return to ANALYST.
- CHECKER_B finds weak source citation -> return to ANALYST or CHECKER_B depending on ownership.
- WRITER cites RAW evidence -> return to WRITER, and if needed CHECKER_B.
- GATEKEEPER finds unsupported conclusion -> return to WRITER or ARCHITECT.

## Completion Rule

The final answer to the user may be delivered only after PACKAGER returns `GATE_RESULT: PASS`, unless the user explicitly asks for a partial interim result.
