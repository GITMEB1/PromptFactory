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

## Recurring anti-pattern checks (release-gate required)
- **AP-001 — Single-Class Source Overreliance**
  - Signal: Major claims rely on one source class only.
  - Detection: Compare `claim_inventory` evidence coverage before scoring.
  - Guardrail: Enforce `rules/source_routing.md` class balancing.
  - Recovery: Require at least one additional qualifying source class for decision-critical claims.
- **AP-002 — Hidden Staleness**
  - Signal: Sources outside policy window appear without explicit caveats.
  - Detection: Check freshness metadata and disclosure text in draft.
  - Guardrail: Apply `rules/freshness_policy.md` and `prompts/freshness_checker.md`.
  - Recovery: Downgrade confidence, add staleness disclosure, and prefer newer replacements where available.
- **AP-003 — Premature Certainty Under Conflict**
  - Signal: Draft presents a single definitive answer while source disagreement remains unresolved.
  - Detection: Cross-check conflict notes against conclusion language.
  - Guardrail: Route via `prompts/source_conflict_resolver.md` and `rules/conflict_resolution.md`.
  - Recovery: Require explicit conflict disclosure, rationale, and residual uncertainty statement.
- **AP-004 — Generic/Non-actionable Feedback**
  - Signal: Evaluator notes cannot be tied to a draft location and rule.
  - Detection: Review `blocking_issues` and `non_blocking_improvements` for traceability.
  - Guardrail: Every issue must include location + violated rule/policy.
  - Recovery: Re-run with structured fix list entries.
- **AP-005 — Severity Miscalibration**
  - Signal: Critical policy violations labeled as non-blocking edits.
  - Detection: Compare issue severity to release risk and policy class.
  - Guardrail: Apply blocking/non-blocking thresholds consistently.
  - Recovery: Reclassify issue severity before final verdict.
- **AP-006 — Regression Blindness**
  - Signal: Same defects recur across revisions without explicit comparison.
  - Detection: Diff current evaluator output against prior report when available.
  - Guardrail: Include a regression checkpoint in evaluation procedure.
  - Recovery: Add a targeted regression fix list before pass recommendation.

## Schema references
- `schemas/eval_record.md` — structured evaluation output and issue tracking.
- `schemas/approval_manifest.md` — gate decision and sign-off structure when escalation or approval is needed.
