# Schema — response_plan

Structured plan for final drafting from approved claims.

## Template
```yaml
response_plan:
  plan_id: "RP-<task_id>"
  objective: ""
  section_order:
    - section_id: ""
      purpose: ""
      mapped_claim_ids: []
      disclosure_slots: []
  coverage_matrix:
    - user_need: ""
      claim_ids: []
  open_issues: []
```

## Filled example
```yaml
response_plan:
  plan_id: "RP-T-20260311-promptfactory-schemas"
  objective: "Deliver schema files and documentation cross-references."
  section_order:
    - section_id: "S1"
      purpose: "Summarize schema additions"
      mapped_claim_ids: ["C-001"]
      disclosure_slots: []
    - section_id: "S2"
      purpose: "Summarize where cross-references were added"
      mapped_claim_ids: ["C-002"]
      disclosure_slots: ["note on unchanged policy behavior"]
  coverage_matrix:
    - user_need: "Schema templates + examples"
      claim_ids: ["C-001"]
    - user_need: "Cross-references in workflow/prompt docs"
      claim_ids: ["C-002"]
  open_issues: []
```
