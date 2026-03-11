# Lesson Log

Capture reusable lessons learned from completed runs.

**Schema alignment:** each entry uses exact key names from `schemas/lesson_record.md`.

## Entry Template

```yaml
lesson_record:
  lesson_id: "L-YYYYMMDD-01"
  task_id: "T-YYYYMMDD-001"
  run_id: "R-YYYYMMDD-001"
  what_worked:
    - "Practice or decision that improved quality"
  what_failed:
    - "Failure to avoid next run"
  root_causes:
    - "Why the failure happened"
  reusable_patterns:
    - "Rule to reuse in future runs"
  prompt_or_policy_updates:
    - "prompts/evaluator.md: add anti-pattern check"
  owner: "agent-or-human"
```

## Quick Tag Legend

- `FRESHNESS` — Recency checks and staleness communication
- `CLASS_MIX` — Source-class balancing issues
- `CLAIM_SCOPE` — Over/under-claimed conclusions
- `UNCERTAINTY` — Missing or excessive caveats
