# Prompt Module — Task Intake

## When invoked
- First module in every run, before source routing or retrieval.
- Triggered whenever a new user request, revision request, or scope change arrives.
- Requires the latest user request text and current policy baseline to be available.

## Inputs
- **Required**
  - User request (verbatim).
  - Task context already provided in-session (constraints, target format, audience).
  - Active operating mode hint, if supplied by user (`lightweight` or `deep`).
- **Optional**
  - Prior run artifacts (claim inventory, evaluator notes, critic notes).
  - Repository-specific governance constraints.

## Procedure
1. Parse the request into: objective, deliverable type, constraints, and success criteria.
2. Classify the task profile (risk, freshness sensitivity, compliance sensitivity, ambiguity level).
3. Determine whether a simple answer path is acceptable or a claim-driven path is required.
4. Detect missing inputs that block high-confidence execution.
5. Produce explicit intake assumptions and mark each as confirmed or unconfirmed.
6. Hand off routing requirements to `source_router` and mode recommendation to `lightweight_mode`/`deep_mode`.

## Outputs
- `task_profile`:
  - objective
  - deliverable_type
  - risk_level
  - freshness_level
  - ambiguity_level
- `intake_assumptions` (with confirmation status).
- `missing_information_requests` (if any).
- `mode_recommendation` with rationale.

## Quality checks
- Objective and deliverable are both explicitly stated.
- At least one risk/freshness classification is recorded.
- All assumptions are labeled confirmed vs unconfirmed.
- Blocking gaps are surfaced instead of silently ignored.

## Failure patterns
- **Symptom:** Work starts with no clear deliverable shape.
  - Cause: Objective parsing skipped or too vague.
  - Fix: Re-run intake with explicit output template.
- **Symptom:** Wrong mode selected for high-stakes task.
  - Cause: Risk/freshness misclassification.
  - Fix: Escalate to `deep_mode` and re-run routing.
- **Symptom:** Hidden assumptions appear late in composition.
  - Cause: Intake assumptions not externalized.
  - Fix: Regenerate `intake_assumptions` before retrieval.
