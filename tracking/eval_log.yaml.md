# Tracking Template — Eval Log

Use this template to capture post-run quality scoring and follow-ups.

**Schema alignment:** each entry nests `eval_record` and uses exact key names from `schemas/eval_record.md`.

```yaml
evaluations:
  - eval_record:
      eval_id: "EV-<task_id>-01"
      task_id: "T-YYYYMMDD-001"
      draft_id: "D1"
      rubric_scores:
        correctness: 1-5
        completeness: 1-5
        calibration: 1-5
        usability: 1-5
      pass_status: pass|conditional_pass|fail
      blocking_issues:
        - "Blocking issue text"
      non_blocking_improvements:
        - "Improve disclosure wording"
      policy_violations:
        - "rules/freshness_policy.md"
```
