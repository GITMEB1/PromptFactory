# Prompt Module — Lightweight Mode

## Purpose
Execution interface for lightweight runs. This module defines *how* to execute in lightweight mode once selected by the canonical policy path.

## Policy boundary
- Mode selection and escalation authority: [`CANONICAL_EXECUTION_PATH.md`](../CANONICAL_EXECUTION_PATH.md#2-mode-selection-lightweight-vs-deep).
- Governing policy and thresholds remain in canonical/rules documents, not this module.

## Inputs
- `task_profile` and mode decision from canonical intake flow.
- User urgency and verbosity constraints.
- Active stage artifacts produced so far.

## Execution deltas (vs deep mode)
1. Use abbreviated checks scoped to highest-impact user questions.
2. Use minimal viable source coverage that still meets the assigned risk bar.
3. Build a compact claim inventory focused on material claims only.
4. Produce concise synthesis with required caveats.
5. If any canonical escalation trigger appears, hand off immediately to deep mode.

## Outputs
- `lightweight_execution_plan`.
- `compact_claim_inventory`.
- `concise_response_draft`.
- `escalation_flags` (if mode switch needed).
