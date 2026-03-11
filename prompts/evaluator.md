# Prompt Module — Evaluator

## When invoked
- First post-draft validation pass after composition.
- Triggered for objective quality scoring and policy conformance checks.
- Serves as the primary release gate scorer before any adversarial `critic` challenge.

## Inputs
- **Required**
  - `draft_response`.
  - `claim_inventory` and `claim_usage_log`.
  - Canonical policy files:
    - `rules/evaluation_gates.md`
    - `rules/claim_safety.md`
    - `rules/source_discipline.md`
    - `rules/conflict_and_uncertainty.md`
    - `rules/proportionality.md`
- **Optional**
  - Prior evaluator reports for regression comparison.
  - Task-specific scoring rubric.

## Procedure
1. Validate structural compliance with requested format and constraints.
2. Verify each major assertion traces to an approved claim and citation.
3. Consult rule: `rules/evaluation_gates.md`.
4. Execute step: score correctness, completeness, calibration, and usability; classify pass/warn/fail severity.
5. Consult rule: `rules/claim_safety.md`, `rules/source_discipline.md`, `rules/conflict_and_uncertainty.md`, `rules/proportionality.md`.
6. Execute step: log blocking vs non-blocking issues with draft locations and fix actions.
7. Execute step: recommend pass, conditional pass (with fixes), or fail.
8. Execute step: forward unresolved risk concentrations to `critic` for adversarial stress testing.

## Outputs
- `evaluation_report`:
  - rubric_scores
  - pass_status
  - blocking_issues
  - non_blocking_improvements
- `fix_list` prioritized by impact.

## Quality checks
- Report includes explicit pass/fail rationale.
- Blocking issues are actionable and traceable to draft locations.
- Scoring dimensions are completed, not partial.
- Rule references point only to canonical files under `rules/*`.

## Failure patterns (module-specific)
- **Symptom:** Evaluator calls pass without enforcing hard gates.
  - Consult rule: `rules/evaluation_gates.md`.
  - Execute step: Recompute verdict from gate outcomes before release.
- **Symptom:** Findings are generic and non-actionable.
  - Consult rule: `rules/claim_safety.md`.
  - Execute step: Reissue findings with draft location, violated rule, and concrete fix.
- **Symptom:** Confidence label conflicts with unresolved disagreement.
  - Consult rule: `rules/conflict_and_uncertainty.md`.
  - Execute step: Downgrade confidence and require explicit uncertainty disclosure.
- **Symptom:** Workflow depth is mismatched to task stakes.
  - Consult rule: `rules/proportionality.md`.
  - Execute step: Reclassify as blocking/non-blocking based on stake level.

## Schema references
- `schemas/eval_record.md` — structured evaluation output and issue tracking.
- `schemas/approval_manifest.md` — gate decision and sign-off structure when escalation or approval is needed.
