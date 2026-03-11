# Tracking Template — Tasks

Use this template to track incoming work before execution.

```yaml
tasks:
  - task_id: T-YYYYMMDD-001
    created_at_utc: "2026-01-14T09:15:00Z"
    owner: "agent-or-human"
    requester: "team-or-user"
    objective: "One-sentence target outcome"
    constraints:
      - "Formatting requirements"
      - "Forbidden actions"
    deliverables:
      - "file/path.md"
      - "schema/update.yaml"
    risk_level: low|medium|high
    risk_notes:
      - "Primary uncertainty"
    dependencies:
      - task_id: T-YYYYMMDD-000
        type: blocks|blocked_by|related
    status: queued|in_progress|blocked|done
    routing_hint:
      mode: lightweight|deep
      likely_modules:
        - prompts/task_intake.md
        - prompts/source_router.md
    freshness_requirements:
      recency_window: "<= 90 days"
      requires_explicit_date_check: true
    completion_criteria:
      - "All deliverables updated"
      - "Eval score >= 4 on grounding"
```
