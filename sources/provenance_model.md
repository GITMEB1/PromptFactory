# Provenance Model

Defines how claims map to sources, how citations are attached, and how conflicts are recorded.

## Citation Granularity
- **Atomic claim level** by default: each materially testable statement should map to at least one source.
- **Paragraph-level citation** is acceptable only when all contained claims share the same evidence set.
- **Composite claims** must list every source class contributing unique support.

## Claim-to-Source Traceability
For each claim, capture:
- Claim ID (stable within a run).
- Source IDs supporting the claim.
- Support type: direct evidence / inferential synthesis / contextual constraint.
- Retrieval timestamp (for live sources).
- Confidence annotation (high/medium/low).

### Minimal Trace Record (template)
```yaml
claim_id: C-001
text: "Feature X is unavailable on plan Y as of 2026-03-01."
sources: [S-official-12, S-retrieval-03]
support_type: direct_evidence
retrieved_at: 2026-03-01T14:25:00Z
confidence: high
```

## Conflict Annotation
When sources disagree:
- Create a conflict note with conflict ID.
- Identify competing claims and source IDs.
- Classify conflict type (temporal, scope, measurement, definitional).
- Resolve using precedence (`private_context` constraints, then `official`, then corroborated retrieval/practitioner).
- Preserve unresolved conflicts explicitly in user-facing output.

### Conflict Record (template)
```yaml
conflict_id: X-004
claim_a: C-010
claim_b: C-011
sources_a: [S-official-07]
sources_b: [S-practitioner-02, S-retrieval-08]
conflict_type: temporal
resolution: "Prefer official source dated later; mark practitioner claim as outdated."
status: resolved
```
