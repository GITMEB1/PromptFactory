# Schema — lesson_record

Post-run learning artifact for continuous improvement.

## Template
```yaml
lesson_record:
  lesson_id: "L-<YYYYMMDD>-<nn>"
  task_id: ""
  run_id: ""
  what_worked: []
  what_failed: []
  root_causes: []
  reusable_patterns: []
  prompt_or_policy_updates: []
  owner: ""
```

## Filled example
```yaml
lesson_record:
  lesson_id: "L-20260311-01"
  task_id: "T-20260311-promptfactory-schemas"
  run_id: "R1"
  what_worked:
    - "Using compact YAML-first schemas reduced ambiguity in module handoffs."
    - "Embedding one concrete example per schema accelerated consistency checks."
  what_failed: []
  root_causes: []
  reusable_patterns:
    - "For every new artifact type, define template + filled example together."
  prompt_or_policy_updates:
    - "Reference schemas directly in module output sections."
  owner: "codex"
```
