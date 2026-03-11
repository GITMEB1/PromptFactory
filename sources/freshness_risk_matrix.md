# Freshness Risk Matrix

This matrix defines when retrieval is required and how to handle stale-risk.

## Risk Bands
- **Low stale risk**: foundational concepts, stable standards, long-lived invariants.
- **Medium stale risk**: tooling defaults, minor version behavior, common best practices.
- **High stale risk**: pricing, availability, policy/legal terms, incidents, model/version releases.

## Retrieval Thresholds

| Claim Stale Risk | Max Acceptable Age (without fresh retrieval) | Retrieval Requirement | Corroboration Requirement |
|---|---:|---|---|
| Low | 180 days | Optional | 1 source acceptable |
| Medium | 30 days | Required if claim affects user decision materially | Prefer 2 independent sources |
| High | 7 days (or same-day for incidents/pricing/policy changes) | Mandatory | 2+ sources, one ideally official |

## Stale-Risk Handling
1. Classify each consequential claim into low/medium/high stale risk.
2. If source age exceeds threshold, mark claim as **stale-risk** and trigger retrieval.
3. If retrieval unavailable, degrade output:
   - Convert assertions into conditional language.
   - Add explicit verification step for user.
   - Avoid prescriptive guidance for high-risk decisions.
4. Record retrieval timestamp and source version metadata in provenance notes.

## Override Rules
- High-impact + high-uncertainty claims always require retrieval, even if existing docs are recent.
- Private context may shorten thresholds when internal systems change rapidly (e.g., daily deploys).
