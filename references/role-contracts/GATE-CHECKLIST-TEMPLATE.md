# Gate Checklist Template — Sisyphus-Checkable Persona Contract

Append a `Machine Contract (Sisyphus)` section to each persona file using this shape. Keep the existing prose; the machine contract makes the existing gate checkable.

## Template

```markdown
## Machine Contract (Sisyphus)

Reference schema: `references/role-contracts/SCHEMA.md`

### Inputs Required
- [ ] INPUT_<PERSONA>_01: <required upstream artifact> | source: <prior OUTPUT_* or user approval>

### Outputs Required
- [ ] OUTPUT_<PERSONA>_01: <artifact this persona must produce> | format: <file/table/section/envelope>

### Pass Criteria
- [ ] GATE_<PERSONA>_01: <verifiable condition>

### Fail / Repair Triggers
- `MISSING_INPUT`: <condition> -> repair_request_to: <persona>
- `GATE_FAIL`: <condition> -> repair_request_to: <persona>

### Required Handoff Envelope
The persona response must end with `SISYPHUS_HANDOFF_ENVELOPE` and exactly one `GATE_RESULT:` token.
```

## Worked Example — CHECKER_A

```markdown
## Machine Contract (Sisyphus)

Reference schema: `references/role-contracts/SCHEMA.md`

### Inputs Required
- [ ] INPUT_CKA_01: ANALYST evidence log | source: OUTPUT_ANL_01
- [ ] INPUT_CKA_02: calculation log when formulas exist | source: OUTPUT_ANL_02

### Outputs Required
- [ ] OUTPUT_CKA_01: number-checked evidence log | format: evidence log with checker notes
- [ ] OUTPUT_CKA_02: number failure list | format: repair list or `none`

### Pass Criteria
- [ ] GATE_CKA_01: every numeric row has value, unit, year, and source tier
- [ ] GATE_CKA_02: every formula row has traceable inputs
- [ ] GATE_CKA_03: smell test completed for totals and shares

### Fail / Repair Triggers
- `MISSING_INPUT`: evidence log absent -> repair_request_to: ANALYST
- `NUMBER_FAILURE`: unit, year, formula, or smell test failure -> repair_request_to: ANALYST
- `GATE_FAIL`: checker cannot mark rows as number-checked -> repair_request_to: CHECKER_A

### Required Handoff Envelope
The response must end with `SISYPHUS_HANDOFF_ENVELOPE` and `GATE_RESULT: PASS`, `GATE_RESULT: FAIL`, or `GATE_RESULT: PARTIAL`.
```
