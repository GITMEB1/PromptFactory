# Prompt Module — Retrieval Reader

## When invoked
- After `source_router` has produced a retrieval queue.
- Triggered whenever retrieved or attached materials need structured extraction.
- Requires source metadata and class labels for each artifact.

## Inputs
- **Required**
  - Retrieved content and/or attached documents.
  - `source_plan` and class precedence.
  - Extraction target list (claims/questions to support).
- **Optional**
  - Prior extraction notes for incremental updates.
  - Freshness and credibility thresholds.

## Procedure
1. Triage materials by class relevance and authority.
2. Extract only statements that directly support or challenge target claims.
3. Record citation-ready snippets with source identity and timestamp.
4. Tag each extraction with confidence and scope limits.
5. Separate normative guidance, empirical findings, and anecdotal practitioner notes.
6. Forward disputed or contradictory extracts to `source_conflict_resolver`.

## Outputs
- `evidence_notes` entries containing:
  - claim_target
  - extracted_statement
  - source_reference
  - timestamp_or_version
  - confidence_tag
- `unsupported_targets` list.
- `conflict_candidates` list.

## Quality checks
- Each extracted statement maps to a specific target claim/question.
- Citation metadata is complete enough for downstream referencing.
- Low-confidence or out-of-scope evidence is explicitly tagged.
- Unsupported targets are listed, not silently dropped.

## Failure patterns
- **Symptom:** Large copied passages with low signal.
  - Cause: No target-driven extraction filter.
  - Fix: Enforce claim-target mapping per note.
- **Symptom:** Strong statements without provenance.
  - Cause: Citation metadata omitted.
  - Fix: Reject extraction row until metadata is complete.
- **Symptom:** Contradictions leak into final draft.
  - Cause: Conflict candidates not escalated.
  - Fix: Route to `source_conflict_resolver` before claim building.
