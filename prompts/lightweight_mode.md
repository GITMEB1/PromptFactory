# Prompt Module — Lightweight Mode

## When invoked
- Selected when task risk is low and turnaround speed is prioritized.
- Triggered by intake mode recommendation or explicit user request.
- Requires confirmation that lightweight constraints are policy-safe.

## Inputs
- **Required**
  - `task_profile` with low-to-moderate risk assessment.
  - User urgency and verbosity constraints.
  - Minimum evidence requirements.
- **Optional**
  - Prior validated patterns for similar tasks.
  - User-approved assumptions to avoid over-retrieval.

## Procedure
1. Limit scope to highest-impact user questions.
2. Use minimal viable source set per routing policy.
3. Build compact claim inventory with strict support threshold.
4. Compose concise response with direct recommendations.
5. Run abbreviated evaluator checks focused on critical errors.
6. Escalate to `deep_mode` if conflicts, high uncertainty, or policy triggers appear.

## Outputs
- `lightweight_execution_plan`.
- `compact_claim_inventory`.
- `concise_response_draft`.
- `escalation_flags` (if mode switch needed).

## Quality checks
- Response addresses core user objective without unnecessary depth.
- Critical claims remain evidence-backed.
- Time-saving shortcuts do not violate policy gates.
- Escalation criteria are explicitly evaluated.

## Failure patterns
- **Symptom:** Fast answer is brittle or wrong.
  - Cause: Over-pruned evidence path.
  - Fix: Expand route or switch to deep mode.
- **Symptom:** Concision removes necessary caveats.
  - Cause: Uncertainty handling skipped.
  - Fix: Add minimal caveat statements.
- **Symptom:** Lightweight mode used on high-risk tasks.
  - Cause: Intake gating failure.
  - Fix: Require explicit risk recheck before execution.
