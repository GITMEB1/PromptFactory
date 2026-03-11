# Prompt Module — Lightweight Mode

## Trigger
- Use when task risk is low and speed is prioritized.
- Trigger from intake recommendation or explicit user request.

## Inputs
- **Required**
  - `task_profile` with low-to-moderate risk assessment.
  - User urgency and verbosity constraints.
  - Minimum evidence requirements.
  - Canonical policy files:
    - `rules/proportionality.md`
    - `rules/source_discipline.md`
    - `rules/claim_safety.md`
- **Optional**
  - Prior validated patterns for similar tasks.
  - User-approved assumptions to avoid over-retrieval.

## Procedure
1. Consult rule: `rules/proportionality.md`.
2. Execute step: constrain scope to highest-impact user questions.
3. Consult rule: `rules/source_discipline.md`.
4. Execute step: use minimal viable source classes for the stated risk.
5. Consult rule: `rules/claim_safety.md`.
6. Execute step: build a compact claim inventory and reject unsupported claims.
7. Execute step: compose concise recommendations with necessary caveats.
8. Execute step: escalate to `deep_mode` when conflicts, uncertainty, or gate triggers appear.

## Outputs
- `lightweight_execution_plan`.
- `compact_claim_inventory`.
- `concise_response_draft`.
- `escalation_flags` (if mode switch needed).

## Failure patterns
- **Symptom:** Fast answer is brittle or wrong.
  - Consult rule: `rules/source_discipline.md`.
  - Execute step: expand source classes or switch to `deep_mode`.
- **Symptom:** Concision removes required caveats.
  - Consult rule: `rules/conflict_and_uncertainty.md`.
  - Execute step: add minimal uncertainty language before release.
- **Symptom:** Lightweight mode used for high-stakes tasks.
  - Consult rule: `rules/proportionality.md`.
  - Execute step: reclassify task and hand off to `deep_mode`.
