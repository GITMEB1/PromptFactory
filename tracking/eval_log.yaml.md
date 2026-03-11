# Tracking Template — Eval Log

Use this template to capture post-run quality scoring and follow-ups.

```yaml
evaluations:
  - eval_id: E-YYYYMMDD-001
    run_id: R-YYYYMMDD-001
    evaluator: agent|human
    scored_at_utc: "2026-01-14T09:35:00Z"
    rubric_scores:
      grounding: 1-5
      source_quality: 1-5
      freshness_handling: 1-5
      uncertainty_calibration: 1-5
      instruction_compliance: 1-5
    overall_score: 1-5
    verdict: ship|revise|escalate
    strengths:
      - "Clear source-class labeling"
    weaknesses:
      - "Did not quantify staleness impact"
    corrective_actions:
      - action: "Add explicit freshness caveat in final answer"
        owner: "agent"
        due_utc: "2026-01-14T10:00:00Z"
    linked_lessons:
      - tracking/lesson_log.md#L1
```
