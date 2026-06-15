# Role Contract Schema — Sisyphus-Enforced Handoff Envelope

이 문서는 `research-consulting-team` skill 의 모든 persona/sub-agent 산출물이 따라야 하는 공통 envelope 입니다. Sisyphus 는 각 sub-agent 응답의 마지막에 이 envelope 가 있는지 확인하고, `GATE_RESULT:` token 으로 다음 단계 진행 여부를 판단합니다.

## Required Output Rule

모든 persona sub-agent 는 응답 마지막에 아래 fenced block 을 반드시 포함합니다. 실패했을 때도 생략하지 않습니다.

```text
[SISYPHUS_HANDOFF_ENVELOPE]
phase: <phase-number-or-name>
from_persona: <ORCHESTRATOR|SCOPER|ANALYST|CHECKER_A|CHECKER_B|INTEGRATOR|ARCHITECT|CRITIC|WRITER|GATEKEEPER|PACKAGER>
to_persona: <next-persona-or-USER-or-SISYPHUS>
run_id: <run-id-or-session-label>
inputs_received:
  - <input id>: <path, prior envelope field, or user-approved brief section>
outputs_produced:
  - <output id>: <path, table, section, or response artifact>
gate_checks:
  - <GATE_ID>: <PASS|FAIL|PARTIAL> - <short evidence>
GATE_RESULT: <PASS|FAIL|PARTIAL>
gate_failures:
  - <FAIL_CODE or none>: <reason>
repair_request_to: <persona id or none>
handoff_notes: <short notes for next persona>
[/SISYPHUS_HANDOFF_ENVELOPE]
```

## Gate Result Tokens

Sisyphus checks these exact strings. Do not translate or alter them.

- `GATE_RESULT: PASS` — all required inputs, outputs, and pass criteria are satisfied. Sisyphus may advance.
- `GATE_RESULT: FAIL` — at least one required condition failed. Sisyphus must repair or roll back.
- `GATE_RESULT: PARTIAL` — useful partial output exists, but a required condition is missing. Sisyphus must decide whether to run another cycle or ask the user.

## Repair Codes

Use one or more of these codes in `gate_failures`.

| Code | Meaning | Default Sisyphus action |
|---|---|---|
| `MISSING_INPUT` | Required prior artifact is absent or incomplete | Return to prior persona |
| `GATE_FAIL` | Persona-specific quality gate failed | Reinvoke same persona with failures |
| `OUT_OF_SCOPE` | Work drifted outside Research Brief or user-approved scope | Return to ORCHESTRATOR/SCOPER |
| `SECURITY_VIOLATION` | Credential, license, or policy risk detected | Stop and notify user |
| `BRIEF_DRIFT` | Classification, metric, method, or segment changed without approval | Return to SCOPER |
| `EVIDENCE_GAP` | Data is insufficient after required attempts | Mark Insufficient or run another ANALYST cycle |
| `SOURCE_FAILURE` | Source quality, URL, citation, or provenance failed | Return to CHECKER_B or ANALYST |
| `NUMBER_FAILURE` | Unit, date, formula, or smell test failed | Return to CHECKER_A or ANALYST |
| `FORMAT_FAILURE` | Output does not match requested report/view/package format | Return to producing persona |

## Stable Field Conventions

- `GATE_*` IDs are stable and greppable. Do not reuse an ID for a different check.
- `INPUT_*` and `OUTPUT_*` IDs describe cross-phase handoff artifacts. Downstream `INPUT_*` should name the upstream `OUTPUT_*` it depends on.
- Confidence values must follow `references/confidence-rating.md`: `High`, `Medium`, `Low`, `Insufficient`.
- Evidence rows and statuses must follow `references/evidence-log-spec.md`.
- View/table/slide structure must follow `references/view-spec.md` when a view spec exists.

## PASS Example

```text
[SISYPHUS_HANDOFF_ENVELOPE]
phase: 3a
from_persona: CHECKER_A
to_persona: CHECKER_B
run_id: 2026-06-15-example
inputs_received:
  - INPUT_CKA_01: OUTPUT_ANL_01 evidence-log-raw.csv
outputs_produced:
  - OUTPUT_CKA_01: evidence-log-number-checked.csv
gate_checks:
  - GATE_CKA_01: PASS - all numeric rows have unit and year
  - GATE_CKA_02: PASS - smell test completed for market totals
GATE_RESULT: PASS
gate_failures:
  - none: none
repair_request_to: none
handoff_notes: CHECKER_B should verify sources and citation provenance.
[/SISYPHUS_HANDOFF_ENVELOPE]
```

## FAIL Example

```text
[SISYPHUS_HANDOFF_ENVELOPE]
phase: 2
from_persona: ANALYST
to_persona: SISYPHUS
run_id: 2026-06-15-example
inputs_received:
  - INPUT_ANL_01: Research Brief missing Phase C tier threshold
outputs_produced:
  - none: no research started
gate_checks:
  - GATE_ANL_01: FAIL - Brief Phase C.C.4 is empty
GATE_RESULT: FAIL
gate_failures:
  - MISSING_INPUT: Research Brief lacks tier threshold
  - BRIEF_DRIFT: ANALYST cannot infer metric standards
repair_request_to: SCOPER
handoff_notes: Return to SCOPER for Phase C completion before ANALYST work.
[/SISYPHUS_HANDOFF_ENVELOPE]
```
