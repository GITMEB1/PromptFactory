# Prompt Module — Deep Mode

## Purpose
Execution interface for deep runs. This module defines *how* to execute in deep mode once selected or escalated by the canonical policy path.

## Policy boundary
- Mode selection and escalation authority: [`CANONICAL_EXECUTION_PATH.md`](../CANONICAL_EXECUTION_PATH.md#2-mode-selection-lightweight-vs-deep).
- Governing policy and thresholds remain in canonical/rules documents, not this module.

## Inputs
- `task_profile` and mode decision/escalation from canonical intake flow.
- Source/claim/conflict artifacts required by the active workflow stage.
- External review or acceptance criteria when provided.

## Execution deltas (vs lightweight mode)
1. Run full checks across all material claims and workflow stages.
2. Use expanded source coverage with redundancy and freshness-aware retrieval.
3. Perform full claim-to-source traceability and uncertainty/conflict resolution.
4. Execute evaluator/critic remediation loops to closure or explicit deferral.
5. If canonical escalation requires it, hand off to human review/sign-off.

## Outputs
- `deep_execution_record` spanning all module artifacts.
- `high_assurance_claim_inventory` with full traceability.
- `review_ready_response` plus unresolved-risk disclosures.


## Evidence integrity requirements for deep factual validation
For deep-mode factual validation runs:
- Treat required source classes as hard gates, not recommendations.
- Require exact source-level provenance for material claims (title + class/type + reference).
- Reject vague provenance bundles.
- Prevent clean completion if evidence-class satisfaction or artifact accounting is incomplete.
