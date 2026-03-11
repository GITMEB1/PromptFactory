# Retrieval Source Index

Retrieval sources are run-time fetched materials used to verify freshness, resolve uncertainty, and ground high-volatility claims.

## Criteria
- Retrieved during the current run or from a freshness-bounded cache.
- Includes retrievable metadata (timestamp, URL, title, version/etag if available).
- Source quality passes minimal credibility checks for its class.
- Content is sufficiently specific to support cited claims.

## Allowed Usage
- Validate time-sensitive facts (pricing, releases, outages, policy updates).
- Confirm or falsify model-prior and practitioner claims.
- Improve precision for volatile domains where official docs may lag.
- Required for high stale-risk tasks as defined in `sources/freshness_risk_matrix.md`.

## Failure Modes
- **Snapshot drift**: result changed after retrieval timestamp.
- **Ranking bias**: top results not representative of strongest evidence.
- **Mirror contamination**: scraped copies diverge from canonical source.
- **Overfitting to latest**: newest source used without durability checks.
