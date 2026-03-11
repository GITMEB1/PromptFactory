# Evaluation Gates

Compact eval dimensions, lint checks, and release-block logic.

## A) Required evaluation dimensions

Rate each dimension as `pass`, `warn`, or `fail`.

| Dimension | Fail condition |
|---|---|
| Source discipline | Risk-to-source routing violated or prohibited source-class use |
| Freshness control | Volatile/high-risk claims not date-verified or uncertainty-adjusted |
| Claim safety | Unsupported/orphan claims, missing provenance minimums |
| Conflict handling | Relevant disagreement ignored or unresolved conflict hidden |
| Uncertainty calibration | Confidence language inconsistent with evidence quality |
| Clarity/actionability | Guidance too vague for decision use |
| Proportionality | Depth/overhead materially mismatched to task stakes |

## B) Lint checks (minimum set)

| Check ID | Severity | Trigger |
|---|---|---|
| unsupported_claims | fail | Material factual claim lacks inventory/provenance linkage |
| stale_high_risk_claims | fail | High-risk/volatile claim lacks recent date anchor |
| ignored_source_conflict | fail | Material conflict not disclosed/adjudicated |
| missing_provenance_fields | fail | Identity/date/locator absent for consequential claims |
| revision_integrity_regression | fail | Rewrite introduced unsourced claims or dropped caveats |
| missing_uncertainty_label | warn | Inference/estimate lacks calibrated confidence |
| practitioner_overgeneralization | warn | Anecdotal practitioner evidence treated as universal |
| note_hygiene_violations | warn | Notes mix labels or unresolved staleness/duplicates |
| disproportional_workflow | warn | Process burden misaligned with task stakes |

## C) Release-block rules

Release is blocked when any condition is true:
- [ ] Any `fail` in source discipline, freshness control, claim safety, or conflict handling.
- [ ] Two or more `fail` ratings across all dimensions.
- [ ] Overall confidence marked high while any critical dimension is `warn/fail`.
- [ ] Known unresolved high-severity conflict without explicit conditional recommendation.

## D) Sign-off checklist

- [ ] Dimension ratings recorded with brief rationale.
- [ ] Remediation action logged for each `warn/fail`.
- [ ] Final confidence aligns with dimension outcomes.
- [ ] Recurrent warning patterns captured for process improvement.
