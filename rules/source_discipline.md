# Source Discipline

## Canonical metadata
- **Decision area owned:** Source selection, credibility weighting, source-class boundaries, and freshness escalation for factual claims.
- **Consulted at which execution stage(s):** Evidence gathering, source validation, and pre-release verification.
- **Non-overrides (what this file does not decide):** Does not set confidence language policy, conflict adjudication outcomes, or workflow depth requirements.
- **Neighbor interactions (which canonical rule docs it pairs with):** Pairs with `claim_safety.md` for provenance completeness, `conflict_and_uncertainty.md` for disagreement handling, and `evaluation_gates.md` for release enforcement.

Operational controls for source routing, credibility, practitioner handling, source-class boundaries, and freshness escalation.

## A) Claim routing by risk and source class

| If claim profile is... | Minimum source requirement | Source-class guardrails | Operator action |
|---|---|---|---|
| Low risk + stable | 1 credible source | Do **not** use model prior as sole factual basis when citation is expected | Cite source; keep check lightweight |
| Medium risk and/or periodic drift | 1 authoritative/primary + 1 corroborating source | Retrieval snippets/private notes require validation against official/practitioner evidence before high-impact use | Record why selected sources are sufficient |
| High risk and/or volatile | 2 independent high-credibility sources, recent when possible | Official/primary evidence preferred; practitioner/private/retrieval can support but not replace authoritative verification | Escalate to live retrieval if evidence is stale or missing |

## B) Credibility scoring and tie-breaks

Checklist per source (pass all applicable):
- [ ] Authority/proximity to originating fact.
- [ ] Method transparency or verifiable basis.
- [ ] Recency appropriate to volatility.
- [ ] Relevance to jurisdiction/scope/version.
- [ ] Conflict-of-interest disclosed when present.

Tie-break order when sources disagree on quality:
1. Better scope/jurisdiction match.
2. More recent evidence for volatile claims.
3. More direct/primary methodology.
4. Independent corroboration.

## C) Source-class handling rules

| Source class | Default role | Allowed as sole support? | Required qualifiers |
|---|---|---|---|
| Official / regulator / maintainer / primary publication | Anchor evidence for factual/consequential claims | Yes (low/medium risk if freshness acceptable) | Date + scope |
| Practitioner (operator writeups, postmortems, talks) | Operational nuance, failure modes, implementation constraints | Only for low-stakes troubleshooting with close environment match | Environment, scale, version, transferability caveat |
| Private context (internal docs/notes) | Context and constraints | No, unless provenance and authority are clear and stakes permit | Role/date/context + access limitation note |
| Retrieval extract/snippet | Discovery and candidate evidence | No | Must be traced to full source before material use |
| Model prior | Gap-filling for structure/general background | No for material factual claims | Label as unsourced prior/assumption |

## D) Freshness triggers

Escalate freshness verification when any trigger is true:
- [ ] Topic is pricing, policy/regulation, product capability, incident status, deadlines, or fast-moving guidance.
- [ ] Claim materially affects decisions or safety.
- [ ] Citation date is missing or older than task tolerance.
- [ ] Sources conflict on current state.

Freshness action table:

| Freshness class | Verification expectation | Output requirement |
|---|---|---|
| Stable | Canonical source acceptable even if older | Keep date context when useful |
| Periodic | Prefer recent source/update metadata | Date-anchor statements |
| Volatile | Live/recent check required | If unverified, reduce confidence and state verification gap |

## E) Release gate

Block release if any item fails:
- [ ] Material claim lacks source class appropriate to risk.
- [ ] Prohibited sole-support source class used (practitioner/private/retrieval/model prior for high-stakes fact).
- [ ] Volatile/high-risk claim lacks recent date-anchored verification or explicit uncertainty downgrade.

## F) Deep-mode factual validation evidence gate

When `task_intel.workflow_mode=deep` and the task objective is factual validation, the following are **hard requirements** (not guidance):

1. **Required source classes must be explicitly satisfied.**
   - Every class listed in `task_intel.source_constraints.required_classes` must appear in `source_bundle.class_coverage.satisfied`.
   - `official` is satisfied only if at least one `source_record` has `class: official` with concrete `title` and `reference` values.
   - `retrieval` is satisfied only if at least one `source_record` has `class: retrieval` plus non-`n/a` retrieval metadata (`retrieved_at`, retrieval method/context).
   - Implicit coverage (e.g., "search was done") does **not** satisfy class requirements.

2. **Exact provenance is mandatory for material claims.**
   - Vague bundles such as "Various docs", "OpenAI Documentation", or "web sources" are invalid in deep-mode factual validation.
   - Each material claim must resolve to at least one source with exact source-level attribution (title + source type + reference + version/date when available).

3. **Class-aware provenance must be auditable.**
   - Source records must clearly distinguish `official`, `retrieval`, `practitioner`, and `private_context` classes.
   - If a class contributes only context (not direct evidence), mark that explicitly in claim/source mapping instead of implying direct support.

4. **Missing required evidence class is blocking.**
   - If any required class is unsatisfied, release is blocked or downgraded to explicit partial/verification-required output; do not emit clean-pass claims.
