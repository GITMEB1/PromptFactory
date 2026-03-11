# Source Routing Rules

## Scope
Applies to all research, synthesis, and answer-generation workflows that rely on external or internal sources.

## Required behaviors
- Classify each claim by **risk** (`low`, `medium`, `high`) before sourcing.
- Route claim verification to the minimum acceptable source class:
  - `high`: primary, authoritative, and recent sources; use at least two when feasible.
  - `medium`: one authoritative or primary source plus one corroborating source.
  - `low`: one credible source may be sufficient if non-consequential.
- Prefer source proximity: originator > regulator/maintainer > secondary analysis > commentary.
- Log source rationale for non-obvious choices (why this source class was used).
- Escalate to live retrieval when existing context cannot meet risk-level requirements.

## Prohibited behaviors
- Using social summaries, anonymous forums, or AI-generated content as sole support for factual claims.
- Treating convenience sources (e.g., top search snippets) as authoritative without validation.
- Reusing stale citations for time-sensitive claims without freshness review.
- Downgrading source class to save time on high-risk claims.

## Exceptions
- When authoritative sources are unavailable, use best-available evidence and explicitly mark confidence as limited.
- For clearly opinion-based prompts, route to representative viewpoints rather than factual authority, while labeling interpretation.
- In constrained environments (offline/no browse), provide conditional guidance and identify missing verification steps.

## Audit checks
- Every material factual claim maps to at least one cited source appropriate to risk tier.
- High-risk claims show evidence of multi-source or equivalent-depth validation.
- Source selection notes exist for edge cases or non-standard routing decisions.
- No claim relies exclusively on prohibited source classes.
