# Schema — source_conflict_record

Structured record for conflict adjudication from `prompts/source_conflict_resolver.md`.

## Template
```yaml
source_conflict_record:
  conflict_id: "X-<nnn>"
  task_id: ""
  claim_ids: []
  competing_sources:
    - source_id: ""
      position_summary: ""
  severity: low|medium|high
  resolution_status: resolved|split_outcome|unresolved
  rationale: ""
  winning_or_split_outcome: ""
  residual_uncertainty: ""
```

## Filled example
```yaml
source_conflict_record:
  conflict_id: "X-001"
  task_id: "T-20260311-promptfactory-schemas"
  claim_ids: ["C-002"]
  competing_sources:
    - source_id: "S-private-01"
      position_summary: "Cross-reference all related workflow and prompt docs."
    - source_id: "S-private-03"
      position_summary: "Only update one file to minimize change size."
  severity: medium
  resolution_status: resolved
  rationale: "Task instruction explicitly requires cross-referencing each schema."
  winning_or_split_outcome: "Applied broad doc references across workflow + prompt modules."
  residual_uncertainty: "none"
```
