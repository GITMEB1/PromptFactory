# Prompt Module — Critic

## When invoked
- After `evaluator` identifies residual risk or when task risk requires adversarial challenge.
- Triggered to challenge conclusions with counterfactuals and edge-case stress tests.
- Not used for baseline scoring, formatting checks, or policy lint already owned by `evaluator`.

## Inputs
- **Required**
  - `draft_response` or `final_answer` candidate.
  - `evaluation_report` (to avoid duplicating evaluator checks).
  - Decision-critical claims and assumptions.
- **Optional**
  - `source_conflict_record` and `uncertainty_flags`.
  - Historical failure patterns for similar tasks.

## Procedure
1. Select key conclusions and state the strongest plausible counterposition for each.
2. Run counterfactual probes ("what would make this conclusion wrong?").
3. Stress-test recommendations against edge scenarios and boundary conditions.
4. Identify harms or failure modes that appear only under stressed assumptions.
5. Return targeted adversarial revisions or escalation recommendation.

## Outputs
- `critique_report`:
  - counterfactual_challenges
  - edge_risk_findings
  - assumption_breakpoints
  - adversarial_revision_requests
- `escalation_decision` (proceed, revise, or defer pending evidence).

## Quality checks
- Report includes substantive counterpositions for decision-critical conclusions.
- Findings are adversarial (counterfactual/edge-risk), not generic style or rubric feedback.
- Boundary conditions are explicit for each major recommendation.
- Escalation decision is evidence-aware and justified.

## Failure patterns
- **Symptom:** Critic repeats evaluator comments.
  - Cause: Adversarial scope not enforced.
  - Fix: Restrict output to counterfactual and edge-risk findings.
- **Symptom:** No realistic breakpoints identified.
  - Cause: Stress tests too abstract.
  - Fix: Add concrete scenario probes tied to user context.
- **Symptom:** Endless critique loops.
  - Cause: No clear proceed/defer threshold.
  - Fix: Require explicit escalation decision with trigger conditions.

## Schema references
- `schemas/delta_record.md` — revision-delta tracking for critique loops.
- `schemas/lesson_record.md` — lessons capture after adversarial findings are resolved.
