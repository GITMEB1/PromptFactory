# Prompt Module — Uncertainty Writer

## When invoked
- After claim support status and conflict outcomes are known.
- Triggered when any claim is provisional, contested, or scope-limited.
- Requires uncertainty flags and target audience sensitivity.

## Inputs
- **Required**
  - `uncertainty_flags` and `residual_uncertainty_flags`.
  - Audience profile (technical depth, decision urgency).
  - Draft sections where uncertain claims appear.
- **Optional**
  - House style guidance for confidence language.
  - User preference for concise vs explicit caveats.

## Procedure
1. Classify uncertainty type (evidence gap, conflict, freshness risk, extrapolation).
2. Choose calibrated language patterns for each uncertainty type.
3. Insert caveats at point-of-use, not only in a global disclaimer.
4. Pair caveats with practical next-step actions where possible.
5. Ensure uncertainty language is specific, not evasive.
6. Return an uncertainty language pack for composition/final formatting.

## Outputs
- `uncertainty_language_pack` mapped by claim or section.
- `caveat_placement_map`.
- `follow_up_questions` for reducing uncertainty.

## Quality checks
- Uncertainty statements identify what is unknown and why.
- Caveats are co-located with affected recommendations.
- Language remains decision-useful (not alarmist or dismissive).
- Follow-up actions are concrete when uncertainty is material.

## Failure patterns
- **Symptom:** Blanket disclaimer with no local caveats.
  - Cause: Centralized-only uncertainty handling.
  - Fix: Add section-level caveat placement.
- **Symptom:** False precision in weakly supported claims.
  - Cause: Confidence language not calibrated.
  - Fix: Apply uncertainty language templates by support status.
- **Symptom:** User cannot act due to vague caution.
  - Cause: No follow-up pathway provided.
  - Fix: Attach next-step validation actions.
