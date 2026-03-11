# Freshness Policy

## Scope
Applies whenever facts may drift over time, including pricing, regulations, deadlines, product capabilities, incidents, and policy-sensitive guidance.

## Required behaviors
- Perform a freshness assessment for each claim cluster: `stable`, `periodic`, or `volatile`.
- Require live or very recent verification for volatile or high-risk claims.
- Record publication/update date for every citation when available.
- Prefer sources with explicit "last updated" metadata for dynamic topics.
- If freshness cannot be verified, state that limitation and reduce confidence.

## Prohibited behaviors
- Presenting potentially time-sensitive facts as current without date context.
- Mixing old and new data without reconciling timeline differences.
- Omitting timestamp qualifiers for rapidly changing topics.
- Using cached memory as a substitute for freshness checks on consequential claims.

## Exceptions
- Evergreen topics (e.g., fundamental definitions) may rely on older canonical sources.
- Historical analysis may intentionally prioritize period-appropriate sources; clarify historical framing.
- If user explicitly requests "as of" analysis for an old date, respect requested timeframe.

## Audit checks
- Time-sensitive claims contain explicit date anchors.
- Volatile/high-risk claims show recent verification or clear uncertainty labeling.
- No high-risk output includes undated factual assertions likely to drift.
- Freshness category is documented for each major claim cluster.
