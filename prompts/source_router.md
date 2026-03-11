# Prompt Module — Source Router

## When invoked
- Immediately after `task_intake`, before any evidence extraction.
- Triggered when source classes must be selected or revised.
- Requires task profile and applicable source routing policies.

## Inputs
- **Required**
  - `task_profile` from intake.
  - User-provided materials (if any).
  - Source-class policy constraints (`official`, `practitioner`, `private_context`, `retrieval`, `model_prior`).
- **Optional**
  - Previous route plan from prior run.
  - Known source availability constraints.

## Procedure
1. Map task claims likely needed to source classes with precedence.
2. Determine minimum required classes to satisfy reliability for task risk level.
3. Define prohibited or de-prioritized classes for this task.
4. Set recency requirements and trigger `freshness_checker` when needed.
5. Emit retrieval plan by class, including why each class is included.
6. If class-level disagreement risk is high, pre-register `source_conflict_resolver`.

## Outputs
- `source_plan`:
  - selected_classes
  - class_precedence
  - exclusion_rules
  - recency_requirements
- `retrieval_queue` by source class.
- `conflict_watchlist` for likely disputed claim areas.

## Quality checks
- Every selected class has a task-specific rationale.
- At least one authoritative class exists for high-risk claims.
- Model-prior-only paths are rejected unless explicitly allowed.
- Recency requirements are explicit for freshness-sensitive tasks.

## Failure patterns
- **Symptom:** Over-reliance on one weak source class.
  - Cause: No class diversification in route planning.
  - Fix: Rebuild with policy-conformant class mix.
- **Symptom:** Retrieval gathers irrelevant evidence.
  - Cause: Claim-to-class mapping was underspecified.
  - Fix: Add claim categories and reroute.
- **Symptom:** Conflicts discovered too late.
  - Cause: Conflict risk not flagged at routing time.
  - Fix: Create upfront `conflict_watchlist`.

## Schema references
- `schemas/source_record.md` — per-source metadata used during class routing and credibility checks.
- `schemas/source_bundle.md` — run-level source package linking sources to claims.
