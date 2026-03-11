# Prompt Module — Evaluator

## When invoked
- First post-draft validation pass after composition.
- Triggered for objective quality scoring and policy conformance checks.
- Serves as the primary release gate scorer before any adversarial `critic` challenge.

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
6. Forward only unresolved risk concentrations to `critic` for adversarial stress testing.

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

## Schema references
- `schemas/eval_record.md` — structured evaluation output and issue tracking.
- `schemas/approval_manifest.md` — gate decision and sign-off structure when escalation or approval is needed.
