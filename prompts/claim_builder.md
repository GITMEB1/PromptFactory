# Prompt Module — Claim Builder

## When invoked
- After evidence extraction is complete enough to support drafting.
- Triggered when a claim inventory is required for controlled composition.
- Requires structured evidence notes and route constraints.

## Inputs
- **Required**
  - `evidence_notes` from retrieval reading.
  - `task_profile` and response objective.
  - Policy constraints on evidence sufficiency.
- **Optional**
  - `conflict_resolutions` from resolver module.
  - Prior claim inventory for revision cycles.

## Procedure
1. Convert evidence notes into atomic, testable claims.
2. Assign support status per claim: supported, contested, provisional, or unsupported.
3. Attach minimum citation set for each supported claim.
4. Mark assumptions and inferential jumps explicitly.
5. Exclude unsupported claims from composition set.
6. Send contested/provisional claims to `uncertainty_writer` for language controls.

## Outputs
- `claim_inventory` with fields:
  - claim_id
  - claim_text
  - support_status
  - citations
  - assumption_flags
- `excluded_claims` with exclusion reason.
- `uncertainty_flags` for downstream writing.

## Quality checks
- Claims are atomic (one proposition per claim).
- Supported claims contain at least one valid citation path.
- Contested claims are not mislabeled as settled.
- Excluded claims are tracked with reasons.

## Failure patterns
- **Symptom:** Composite claims hide weak sub-claims.
  - Cause: Claims not atomized.
  - Fix: Split into atomic units and reassess support.
- **Symptom:** Unsupported statements appear in draft.
  - Cause: Exclusion boundary not enforced.
  - Fix: Gate composition to approved claim IDs only.
- **Symptom:** Confidence overstatement.
  - Cause: Provisional claims treated as definitive.
  - Fix: Apply `uncertainty_writer` controls.
