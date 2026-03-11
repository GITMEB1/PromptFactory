# Private Context Source Index

Private context sources are user/project-specific materials not generally public (e.g., internal docs, runbooks, tickets, architecture notes, local datasets).

## Criteria
- Access is authorized for this run and handling requirements are known.
- Artifact provenance is identifiable (owner/team/date/version).
- Scope relevance is explicit to the user's environment.
- Confidentiality class and redistribution limits are documented.

## Allowed Usage
- Resolve environment-specific behavior and local policy constraints.
- Prioritize project conventions over generic defaults.
- Tie recommendations to concrete system topology, SLAs, and dependencies.
- Use as a high-priority constraint source when conflicting with generic guidance.

## Failure Modes
- **Outdated internal state**: stale runbooks or architecture diagrams.
- **Partial visibility**: missing teams/systems create incorrect conclusions.
- **Access leakage risk**: over-citing sensitive details in outputs.
- **Local-global confusion**: project-specific constraints misapplied as universal advice.
