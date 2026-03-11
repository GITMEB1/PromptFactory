# Prompt Module — Composer

## When invoked
- After `response_assembler` provides an approved blueprint.
- Triggered to generate the user-facing narrative text.
- Requires mapped claims and uncertainty instructions.

## Inputs
- **Required**
  - `response_blueprint`.
  - Approved `claim_inventory` entries.
  - Style constraints (tone, verbosity, audience level).
- **Optional**
  - `uncertainty_language_pack` from `uncertainty_writer`.
  - `practitioner_synthesis_notes` for implementation guidance sections.

## Procedure
1. Draft each section using only mapped, approved claims.
2. Integrate citations/disclosures in-line or in the required house style.
3. Preserve distinction between evidence-backed statements and recommendations.
4. Use calibrated language for contested/provisional claims.
5. Remove unsupported filler and speculative expansions.
6. Emit a complete draft for `evaluator` and `critic` passes.

## Outputs
- `draft_response` aligned to blueprint.
- `claim_usage_log` (claim IDs used per section).
- `open_issues` list for unresolved evidence gaps.

## Quality checks
- No statement appears without a mapped claim source.
- Tone and format align with user constraints.
- Provisional claims use calibrated wording.
- Draft remains faithful to section blueprint.

## Failure patterns
- **Symptom:** Fluent text contains unmapped assertions.
  - Cause: Composer improvised beyond claim set.
  - Fix: Enforce claim usage log validation.
- **Symptom:** Overconfident language in uncertain areas.
  - Cause: Uncertainty controls ignored.
  - Fix: Recompose with `uncertainty_writer` guidance.
- **Symptom:** Evidence lost during simplification.
  - Cause: Aggressive paraphrase dropped support qualifiers.
  - Fix: Reinsert qualifiers and source linkage.

## Schema references
- `schemas/response_plan.md` — composition input plan for section order, mapped claims, and disclosures.
- `schemas/claim_inventory.md` — approved claim set and support statuses.
