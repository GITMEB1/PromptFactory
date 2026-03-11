# Prompt Module — Freshness Checker

## Trigger
- Use during or immediately after source routing for freshness-sensitive tasks.
- Trigger when recency materially affects correctness.

## Inputs
- **Required**
  - `task_profile.freshness_level`.
  - Candidate sources with publication date/version metadata.
  - Canonical policy file: `rules/source_discipline.md`.
- **Optional**
  - Prior freshness assessments.
  - Known domain update cadence.

## Procedure
1. Consult rule: `rules/source_discipline.md`.
2. Execute step: derive claim-category freshness windows from task profile.
3. Execute step: classify evidence as in-window, stale-but-usable, or stale-and-blocking.
4. Execute step: issue refresh requests for stale-and-blocking evidence.
5. Consult rule: `rules/conflict_and_uncertainty.md`.
6. Execute step: attach temporal caveats and confidence downgrades where required.

## Outputs
- `freshness_report` with pass/warn/fail by claim category.
- `refresh_requests` list.
- `temporal_caveat_flags` for drafting.

## Failure patterns
- **Symptom:** Outdated guidance presented as current.
  - Consult rule: `rules/source_discipline.md`.
  - Execute step: enforce freshness gate before claim approval.
- **Symptom:** Endless refreshing with no stop rule.
  - Consult rule: `rules/proportionality.md`.
  - Execute step: cap refresh loops to task-appropriate thresholds.
- **Symptom:** Staleness treatment is inconsistent across claims.
  - Consult rule: `rules/source_discipline.md`.
  - Execute step: apply one severity taxonomy per claim category.
