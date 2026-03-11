# Claim Safety

## Canonical metadata
- **Decision area owned:** Provenance completeness, claim-to-source traceability, composition lock, and revision integrity.
- **Consulted at which execution stage(s):** Draft construction, editing/revision, and pre-release claim audit.
- **Non-overrides (what this file does not decide):** Does not choose source credibility tiers, resolve source conflicts, or set proportional workflow depth.
- **Neighbor interactions (which canonical rule docs it pairs with):** Pairs with `source_discipline.md` for source-class adequacy and `evaluation_gates.md` for lint/release blocking.

Operational controls for provenance, composition lock, revision integrity, and note hygiene minimums.

## A) Provenance minimums (per material claim)

| Field | Required? | Minimum content |
|---|---|---|
| Source identity | Yes | Author/publisher or equivalent owner |
| Date | Yes (if available) | Publication/update date or explicit "date unavailable" |
| Locator | Yes | URL, section, or document locator |
| Claim type | Yes | Quote / paraphrase / synthesis / inference |

Gate: claims missing identity + locator fail by default.

## B) Composition lock

Before finalization, verify all:
- [ ] Every material factual claim maps to claim inventory + provenance fields.
- [ ] No new factual assertion was introduced during polishing.
- [ ] Inferences are labeled as inference (not quoted fact).
- [ ] Time/scope/jurisdiction/confidence qualifiers survived editing.
- [ ] Hypotheticals are clearly marked as hypothetical.

## C) Revision integrity

| Revision type | Required checks |
|---|---|
| Formatting-only | Spot-check no semantic drift |
| Semantic edits/compression/restructure | Re-run claim-to-source alignment + caveat retention |
| Added or replaced facts | Full provenance check + lint-critical checks |
| Emergency patch | Fast fix allowed, then mandatory full validation pass |

Block if revision introduces unsupported claims or drops critical caveats/citations.

## D) Note hygiene minimums

Notes must include:
- [ ] Separation of raw excerpt vs interpretation vs decision.
- [ ] Duplicate/conflicting entries reconciled or explicitly flagged.
- [ ] Staleness marker for time-sensitive notes.
- [ ] Unresolved questions tracked as explicit TODOs.

Do not promote notes to final claims when validation status is missing.

## E) Release gate

Fail release when any is true:
- [ ] Orphan factual assertions remain.
- [ ] Quote/paraphrase lineage is unclear.
- [ ] Post-revision claim inventory no longer matches evidence.
- [ ] Stale or contradictory notes were used without explicit handling.
