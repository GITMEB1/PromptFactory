# Schema — delta_record

Change delta between revisions to support regression checks.

## Template
```yaml
delta_record:
  delta_id: "DR-<task_id>-<from>-<to>"
  task_id: ""
  from_revision: ""
  to_revision: ""
  changes:
    - artifact: ""
      change_type: add|modify|remove
      summary: ""
      risk_impact: none|low|medium|high
  regressions_detected: []
  follow_up_actions: []
```

## Filled example
```yaml
delta_record:
  delta_id: "DR-T-20260311-promptfactory-schemas-r0-r1"
  task_id: "T-20260311-promptfactory-schemas"
  from_revision: "r0"
  to_revision: "r1"
  changes:
    - artifact: "schemas/*.md"
      change_type: add
      summary: "Added 10 schema templates with concrete examples."
      risk_impact: low
    - artifact: "prompts/*.md + workflow docs"
      change_type: modify
      summary: "Added cross-references to schema artifacts."
      risk_impact: low
  regressions_detected: []
  follow_up_actions: []
```
