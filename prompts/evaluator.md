# Prompt Module — Evaluator

## When invoked
- First post-draft validation pass after composition.
- Triggered for objective quality and policy conformance checks.
- Requires draft text plus underlying claim/evidence artifacts.

## Inputs
- **Required**
  - `draft_response`.
  - `claim_inventory` and `claim_usage_log`.
  - Applicable policy checks (evidence, provenance, freshness, proportionality).
- **Optional**
  - Prior evaluator reports for regression comparison.
  - Task-specific scoring rubric.

## Procedure
1. Validate structural compliance with requested format and constraints.
2. Verify each major assertion traces to an approved claim and citation.
3. Score draft on correctness, completeness, calibration, and usability.
4. Flag policy violations and severity levels.
5. Recommend pass, conditional pass (with fixes), or fail.
6. Forward unresolved weaknesses to `critic` for adversarial stress test.

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
- Policy violations are tied to named rules.

## Failure patterns
- **Symptom:** Generic feedback that cannot be acted on.
  - Cause: Missing location- and rule-level references.
  - Fix: Re-run with structured fix list fields.
- **Symptom:** Severe issues labeled as minor edits.
  - Cause: No severity calibration.
  - Fix: Apply blocking/non-blocking threshold.
- **Symptom:** Repeated regressions across revisions.
  - Cause: Prior evaluator output not compared.
  - Fix: Add regression checkpoint against previous report.
