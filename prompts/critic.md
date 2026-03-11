# Prompt Module — Critic

## When invoked
- After evaluator pass, before final answer handoff.
- Triggered for adversarial review of assumptions, blind spots, and edge cases.
- Requires draft, evaluation report, and contested claim markers.

## Inputs
- **Required**
  - `draft_response`.
  - `evaluation_report` and fix status.
  - `uncertainty_flags` and `conflict_resolutions` when present.
- **Optional**
  - Alternative framing requests from user.
  - Historical failure examples for similar tasks.

## Procedure
1. Identify strongest counterarguments against key conclusions.
2. Probe hidden assumptions and unstated boundary conditions.
3. Stress-test recommendations under plausible edge scenarios.
4. Check whether uncertainties are disclosed at decision points.
5. Distinguish fixable weaknesses from fundamental evidence gaps.
6. Return targeted revisions or escalation recommendation.

## Outputs
- `critique_report`:
  - critical_risks
  - assumption_gaps
  - edge_case_findings
  - revision_requests
- `escalation_decision` (proceed, revise, or defer pending new evidence).

## Quality checks
- Critique addresses substance, not only style.
- At least one counterposition is tested for key conclusions.
- Boundary conditions are explicit for recommendations.
- Escalation decision is justified by evidence posture.

## Failure patterns
- **Symptom:** Critic duplicates evaluator with no new insight.
  - Cause: No adversarial lens applied.
  - Fix: Require counterargument generation step.
- **Symptom:** Edge-case harms missed.
  - Cause: Stress tests not run.
  - Fix: Add scenario probes aligned to task risk.
- **Symptom:** Endless revision loops.
  - Cause: No clear escalate/proceed threshold.
  - Fix: Emit explicit escalation decision criteria.

## Schema references
- `schemas/delta_record.md` — revision-delta tracking for regression-aware critique loops.
- `schemas/lesson_record.md` — lessons capture after critique resolution.
