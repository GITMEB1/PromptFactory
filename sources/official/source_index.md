# Official Source Index

Official sources are first-party artifacts published by the system owner, platform vendor, standards body, or other canonical authority.

## Criteria
- Produced or maintained by the authoritative entity for the claim domain.
- Versioned, dated, or otherwise identifiable for reproducibility.
- Publicly inspectable or internally auditable.
- Stable identifiers (URL, doc ID, spec section, changelog reference).

## Allowed Usage
- **Primary source of truth** for product behavior, policy, legal requirements, and normative definitions.
- Preferred source for high-risk claims (security, compliance, medical, legal, financial).
- Baseline anchor for conflict resolution against non-official sources.
- May be combined with retrieval for freshness when official docs lag real-time changes.

## Failure Modes
- **Staleness**: documentation not updated after shipping changes.
- **Scope mismatch**: official source covers a different region, tier, or version.
- **Ambiguity**: high-level docs omit edge-case behavior.
- **Publication lag**: release notes or APIs changed before docs reflect updates.
