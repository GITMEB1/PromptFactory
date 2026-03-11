# Tracking Template — Runs

Use this template to track each end-to-end execution instance.

**Schema alignment:** `input_task` uses exact `task_intel` keys, `evaluation` uses exact `eval_record` keys, and `revision_delta` uses exact `delta_record` keys.

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
    input_task:
      task_intel:
        task_id: "T-YYYYMMDD-001"
        title: "Short task title"
        user_request_verbatim: "Original request"
        objective: "One-sentence target outcome"
        audience: "team-or-user"
        deliverable_type: "answer"
        risk_level: low|medium|high
        freshness_requirement: stable|moderate|high
        workflow_mode: lightweight|deep
        scope:
          in_scope: []
          out_of_scope: []
        source_constraints:
          required_classes: []
          prohibited_classes: []
          citation_requirements: ""
        success_definition: []
        assumptions: []
        missing_information_requests: []
    evaluation:
      eval_record:
        eval_id: "EV-<task_id>-01"
        task_id: "T-YYYYMMDD-001"
        draft_id: "D1"
        rubric_scores:
          correctness: 1-5
          completeness: 1-5
          calibration: 1-5
          usability: 1-5
        pass_status: pass|conditional_pass|fail
        blocking_issues: []
        non_blocking_improvements: []
        policy_violations: []
    revision_delta:
      delta_record:
        delta_id: "DR-<task_id>-r0-r1"
        task_id: "T-YYYYMMDD-001"
        from_revision: "r0"
        to_revision: "r1"
        changes: []
        regressions_detected: []
        follow_up_actions: []
    outcome:
      status: success|partial|failed
      confidence: low|medium|high
      escalated: false
```
