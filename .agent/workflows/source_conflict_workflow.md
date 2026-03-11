# Source Conflict Workflow

## When to use
Use when two or more sources materially disagree and the task requires a defensible resolution.

## Inputs
- Conflicting claims and source citations
- Source metadata (authority, freshness, scope)
- Decision context and risk tolerance

## Sequence
1. Isolate conflict statements and normalize claim wording.
2. Compare source authority, recency, and applicability.
3. Seek tie-breaker evidence or authoritative clarifications.
4. Resolve conflict (or preserve ambiguity) with explicit rationale.
5. Document impact on downstream output and caveats.

## Outputs
- Conflict resolution record (or unresolved status)
- Updated claim stance with justification
- Required caveats/disclosures for final output

## Failure conditions
- No credible tie-breaker evidence is available.
- Conflict is irreducible within time or access constraints.
- Resolution would exceed acceptable risk tolerance.

## Handoff contract
Before returning to `default_workflow.md`, provide:
1. **Conflict register:** each disputed claim pair/group with citations.
2. **Resolution decision:** accepted claim, rejected claim, or ambiguity preserved.
3. **Rationale chain:** authority/freshness/scope reasoning used.
4. **Downstream constraints:** mandatory caveats and disallowed assertions.
5. **Escalation trigger:** condition that should reopen this workflow.
