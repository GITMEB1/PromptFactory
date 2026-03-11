# Prompt Module — Freshness Checker

## When invoked
- During or immediately after source routing for freshness-sensitive tasks.
- Triggered when recency materially affects correctness.
- Requires source timestamps/versions and task freshness threshold.

## Inputs
- **Required**
  - `task_profile.freshness_level`.
  - Candidate sources with publication date/version.
  - Policy freshness thresholds.
- **Optional**
  - Prior run freshness assessments.
  - Known domain update cadence.

## Procedure
1. Define acceptable evidence age window for each claim category.
2. Compare source timestamps against required window.
3. Flag stale-but-usable sources vs stale-and-blocking sources.
4. Request refreshed retrieval where stale-and-blocking evidence exists.
5. Annotate claims requiring temporal caveats.
6. Return freshness status to routing and claim modules.

## Outputs
- `freshness_report` with pass/warn/fail by claim category.
- `refresh_requests` list.
- `temporal_caveat_flags` for drafting.

## Quality checks
- Freshness window is explicit and task-specific.
- All critical sources have timestamp/version metadata.
- Blocking staleness results in retrieval refresh request.
- Temporal caveats are attached to affected claims.

## Failure patterns
- **Symptom:** Outdated guidance presented as current.
  - Cause: Timestamp checks skipped.
  - Fix: Enforce freshness gate before claim approval.
- **Symptom:** Endless refreshing with no stop rule.
  - Cause: No claim-category freshness window.
  - Fix: Define bounded recency thresholds.
- **Symptom:** Staleness handled inconsistently.
  - Cause: No stale-but-usable distinction.
  - Fix: Classify stale evidence severity explicitly.
