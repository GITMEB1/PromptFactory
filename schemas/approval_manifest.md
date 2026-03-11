# Schema — approval_manifest

Approval gate record for release decisions in deep-mode or high-risk tasks.

## Template
```yaml
approval_manifest:
  manifest_id: "AM-<task_id>-<run_id>"
  task_id: ""
  run_id: ""
  gate_decisions:
    - gate: intake_completeness|mode_selection|evidence_sufficiency|policy_compliance
      status: pass|conditional_pass|fail
      reviewer: ""
      rationale: ""
      required_actions: []
  final_disposition: approved|approved_with_conditions|blocked
  signoff:
    approver: ""
    approved_at: "<ISO-8601|pending>"
```

## Filled example
```yaml
approval_manifest:
  manifest_id: "AM-T-20260311-promptfactory-schemas-R1"
  task_id: "T-20260311-promptfactory-schemas"
  run_id: "R1"
  gate_decisions:
    - gate: intake_completeness
      status: pass
      reviewer: "codex"
      rationale: "All required fields were derived from user request."
      required_actions: []
    - gate: policy_compliance
      status: pass
      reviewer: "codex"
      rationale: "No policy conflicts detected in documentation-only patch."
      required_actions: []
  final_disposition: approved
  signoff:
    approver: "repository maintainer"
    approved_at: "pending"
```
