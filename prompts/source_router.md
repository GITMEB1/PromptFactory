# Prompt Module — Source Router

## Trigger
- Use immediately after `task_intake`, before evidence extraction.
- Trigger when source classes must be selected or revised.

## Inputs
- **Required**
  - `task_profile` from intake.
  - User-provided materials (if any).
  - Candidate source classes (`official`, `practitioner`, `private_context`, `retrieval`, `model_prior`).
  - Canonical policy files:
    - `rules/source_discipline.md`
    - `rules/proportionality.md`
- **Optional**
  - Previous route plan from prior run.
  - Known source availability constraints.

## Procedure
1. Consult rule: `rules/proportionality.md`.
2. Execute step: set minimum source rigor from task stakes.
3. Consult rule: `rules/source_discipline.md`.
4. Execute step: map likely claim categories to source classes with precedence and exclusions.
5. Execute step: define recency requirements and invoke `freshness_checker` when triggered.
6. Consult rule: `rules/conflict_and_uncertainty.md`.
7. Execute step: pre-register conflict watchlist for likely disputed claim areas.

## Outputs
- `source_plan`:
  - selected_classes
  - class_precedence
  - exclusion_rules
  - recency_requirements
- `retrieval_queue` by source class.
- `conflict_watchlist` for likely disputed claim areas.

## Failure patterns
- **Symptom:** Over-reliance on one weak source class.
  - Consult rule: `rules/source_discipline.md`.
  - Execute step: rebuild route with required class diversification.
- **Symptom:** Retrieval gathers irrelevant evidence.
  - Consult rule: `rules/proportionality.md`.
  - Execute step: tighten claim-category mapping before rerun.
- **Symptom:** Conflicts discovered too late.
  - Consult rule: `rules/conflict_and_uncertainty.md`.
  - Execute step: expand upfront conflict watchlist and route coverage.

## Schema references
- `schemas/source_record.md` — per-source metadata used during class routing and credibility checks.
- `schemas/source_bundle.md` — run-level source package linking sources to claims.
