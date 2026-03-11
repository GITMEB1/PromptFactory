# Schema — claim_inventory

Claim-level artifact produced by `prompts/claim_builder.md`.

## Template
```yaml
claim_inventory:
  task_id: ""
  claims:
    - claim_id: "C-<nnn>"
      text: ""
      support_status: supported|contested|provisional|unsupported
      source_ids: []
      citations: []
      assumption_flags: []
      confidence: low|medium|high
  excluded_claims:
    - claim_text: ""
      exclusion_reason: ""
```

## Filled example
```yaml
claim_inventory:
  task_id: "T-20260311-promptfactory-schemas"
  claims:
    - claim_id: "C-001"
      text: "The request requires 10 schema templates under schemas/."
      support_status: supported
      source_ids: ["S-private-01"]
      citations: ["task instructions in current run"]
      assumption_flags: []
      confidence: high
    - claim_id: "C-002"
      text: "Workflow and prompt docs should link to the new schemas."
      support_status: supported
      source_ids: ["S-private-01"]
      citations: ["task instructions in current run"]
      assumption_flags: []
      confidence: high
  excluded_claims:
    - claim_text: "All existing docs must be rewritten."
      exclusion_reason: "Not requested; out of scope."
```
