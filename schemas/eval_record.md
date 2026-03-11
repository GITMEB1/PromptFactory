# Schema — eval_record

Evaluation output record for `prompts/evaluator.md` runs.

## Template
```yaml
eval_record:
  eval_id: "EV-<task_id>-<nn>"
  task_id: ""
  draft_id: ""
  rubric_scores:
    correctness: 1-5
    completeness: 1-5
    calibration: 1-5
    usability: 1-5
  pass_status: pass|conditional_pass|fail
  evidence_integrity:
    required_source_classes: []
    satisfied_source_classes: []
    missing_source_classes: []
    provenance_quality: exact|mixed|vague
    artifact_accounting_consistent: true|false
  blocking_issues: []
  non_blocking_improvements: []
  policy_violations: []
```

## Filled example
```yaml
eval_record:
  eval_id: "EV-T-20260311-promptfactory-schemas-01"
  task_id: "T-20260311-promptfactory-schemas"
  draft_id: "D1"
  rubric_scores:
    correctness: 5
    completeness: 5
    calibration: 5
    usability: 4
  pass_status: pass
  evidence_integrity:
    required_source_classes: ["private_context"]
    satisfied_source_classes: ["private_context"]
    missing_source_classes: []
    provenance_quality: exact
    artifact_accounting_consistent: true
  blocking_issues: []
  non_blocking_improvements:
    - "Add a schema index link in README for discoverability."
  policy_violations: []
```
