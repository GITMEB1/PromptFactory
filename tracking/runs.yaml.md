# Tracking Template — Runs

Use this template to track each end-to-end execution instance.

```yaml
runs:
  - run_id: R-YYYYMMDD-001
    task_id: T-YYYYMMDD-001
    started_at_utc: "2026-01-14T09:20:00Z"
    completed_at_utc: "2026-01-14T09:31:00Z"
    mode: lightweight|deep
    intake_summary: "Short problem framing"
    module_path:
      - prompts/task_intake.md
      - prompts/source_router.md
      - prompts/claim_builder.md
      - prompts/final_response_builder.md
      - prompts/evaluator.md
    source_classes_used:
      official:
        used: true
        count: 3
      practitioner:
        used: true
        count: 2
      private_context:
        used: false
        count: 0
      model_prior:
        used: true
        count: 1
    freshness_check:
      required: true
      method: "timestamp audit + freshness risk matrix"
      outcome: pass|warn|fail
      notes:
        - "One source older than policy threshold; downgraded confidence"
    output_artifacts:
      - path: "responses/R-YYYYMMDD-001.md"
        type: final_answer
      - path: "tracking/eval_log.yaml.md"
        type: evaluation_record
    outcome:
      status: success|partial|failed
      confidence: low|medium|high
      escalated: false
```
