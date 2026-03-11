# Prompt Module — Source Conflict Resolver

## When invoked
- When evidence extracts contain contradictions across or within source classes.
- Triggered by `conflict_candidates` from retrieval/claim modules.
- Requires source provenance and claim-level conflict statements.

## Inputs
- **Required**
  - Conflicting evidence set with citations.
  - Source class and credibility metadata.
  - Task risk level and decision impact.
- **Optional**
  - Domain-specific conflict resolution policy.
  - User preference for conservative vs progressive stance.

## Procedure
1. Normalize conflicting statements to comparable claim form.
2. Evaluate conflict severity (terminology mismatch vs substantive contradiction).
3. Apply class precedence and credibility criteria.
4. Seek reconciling conditions (scope, date, population, environment).
5. If unresolved, produce explicitly bifurcated claim outcomes.
6. Pass unresolved uncertainty to `uncertainty_writer` for calibrated disclosure.

## Outputs
- `conflict_resolution_log`:
  - conflict_id
  - competing_claims
  - resolution_status
  - rationale
  - winning_or_split_outcome
- `residual_uncertainty_flags`.

## Quality checks
- Every conflict has a documented disposition.
- Resolution rationale cites precedence/credibility basis.
- Unresolved conflicts are not silently collapsed.
- Split outcomes include scope conditions.

## Failure patterns
- **Symptom:** One source chosen without rationale.
  - Cause: Precedence criteria not applied.
  - Fix: Require explicit resolution basis field.
- **Symptom:** Contradictions hidden in final prose.
  - Cause: Unresolved flags dropped.
  - Fix: Pipe residual uncertainty to drafting.
- **Symptom:** False conflict due to scope mismatch.
  - Cause: Claims not normalized.
  - Fix: Add normalization step before adjudication.
