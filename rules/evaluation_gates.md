# Evaluation Gates

## Canonical metadata
- **Decision area owned:** Final quality evaluation dimensions, lint checks, and release-block decisions.
- **Consulted at which execution stage(s):** Final validation/sign-off and any remediation re-check cycle.
- **Non-overrides (what this file does not decide):** Does not replace domain-specific evidence collection, claim authoring, or initial conflict analysis workflows.
- **Neighbor interactions (which canonical rule docs it pairs with):** Pairs with `source_discipline.md`, `claim_safety.md`, `conflict_and_uncertainty.md`, and `proportionality.md` as enforcement surface for their requirements.
- **Cross-file precedence note:** When this file declares a `fail` or release-block condition, that gate authority is binding over advisory guidance elsewhere; advisory guidance remains non-blocking unless elevated here.

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

## E) Sign-off checklist

- [ ] Dimension ratings recorded with brief rationale.
- [ ] Remediation action logged for each `warn/fail`.
- [ ] Final confidence aligns with dimension outcomes.
- [ ] Recurrent warning patterns captured for process improvement.


## D) Deep-mode evidence integrity gates

For deep-mode factual validation runs, these checks are mandatory and release-blocking.

### D1) Required source-class satisfaction (hard fail)
Fail when any class listed in `task_intel.source_constraints.required_classes` is not explicitly present in `source_bundle.class_coverage.satisfied`.

Additional hard checks:
- If `official` is required, fail unless at least one `source_record` has `class: official` with exact `title`, `source_type`, and `reference`.
- If `retrieval` is required, fail unless at least one `source_record` has `class: retrieval` and explicit retrieval metadata (`retrieved_at`, retrieval method/context, and exact reference).

### D2) Provenance precision (hard fail)
Fail when deep-mode factual claims rely on vague provenance labels (for example "Various docs", "OpenAI Documentation", "internet sources") instead of exact source-level entries.

### D3) Artifact accounting consistency (hard fail)
Fail when output artifacts are misreported (for example, run reports separate artifacts while only a consolidated file exists, or vice versa).

### D4) Pass-status ceiling under evidence gaps
- `pass` is forbidden when any D1–D3 issue exists.
- If evidence gaps are unresolved, `pass_status` must be `fail`.
- `conditional_pass` is allowed only when all required classes are satisfied and provenance is exact, with remaining issues non-blocking.
