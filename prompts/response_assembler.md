# Prompt Module — Response Assembler

## When invoked
- After claim inventory is approved for drafting.
- Triggered when claims must be organized into deliverable structure.
- Requires target format and audience constraints.

## Inputs
- **Required**
  - `claim_inventory` (approved subset).
  - Desired output format (brief, memo, step plan, etc.).
  - User constraints (length, tone, required sections).
- **Optional**
  - `uncertainty_flags` and disclosure requirements.
  - Existing outline from prior revision.

## Procedure
1. Build an outline that mirrors user deliverable requirements.
2. Map each section to claim IDs and evidence density expectations.
3. Place uncertainty and limitation disclosures where they are decision-relevant.
4. Sequence sections from high-value conclusions to supporting detail.
5. Ensure all critical user questions are covered by at least one supported claim.
6. Hand off structured draft plan to `composer`.

## Outputs
- `response_blueprint`:
  - section_order
  - section_purpose
  - mapped_claim_ids
  - disclosure_slots
- `coverage_matrix` (user questions ↔ supporting claims).

## Quality checks
- Every section has mapped claim IDs.
- Required user constraints are represented in blueprint.
- No section depends solely on excluded/unsupported claims.
- Uncertainty disclosures are present where needed.

## Failure patterns
- **Symptom:** Draft is coherent but misses user asks.
  - Cause: No coverage matrix.
  - Fix: Reassemble with explicit question coverage.
- **Symptom:** Citations clustered only at end.
  - Cause: Claim mapping to sections was skipped.
  - Fix: Rebind claims per section before composition.
- **Symptom:** Limitations hidden in footnotes.
  - Cause: Disclosure slots not planned.
  - Fix: Promote disclosures to decision-critical sections.

## Schema references
- `schemas/response_plan.md` — section/claim mapping model for output blueprint handoff.
