# Proportionality

## Canonical metadata
- **Decision area owned:** Rigor and process-depth scaling relative to task stakes and user constraints.
- **Consulted at which execution stage(s):** Planning/scoping before analysis and final response shaping before release.
- **Non-overrides (what this file does not decide):** Does not redefine source quality bars, claim provenance fields, or confidence calibration semantics.
- **Neighbor interactions (which canonical rule docs it pairs with):** Pairs with `source_discipline.md` for minimum evidence rigor, `conflict_and_uncertainty.md` for uncertainty verbosity, and `evaluation_gates.md` for mismatch warnings.

Right-size rigor, length, and caveats to stakes and user constraints.

## Decision table

| Task profile | Required rigor | Response shape | Overhead cap |
|---|---|---|---|
| Low stakes, informational | Basic source check + concise uncertainty where needed | Short, direct, minimal caveats | Avoid multi-pass deep workflow |
| Medium stakes, implementation guidance | Corroborated evidence + explicit assumptions | Structured guidance with key caveats | Use targeted checks only |
| High stakes, consequential decisions | Strict source discipline, freshness, conflict adjudication, full claim safety | Evidence-forward recommendation + conditional limits | Full evaluation gates required |

## Anti-pattern checks

- [ ] No over-engineering for low-risk requests.
- [ ] No shallow evidence for high-impact recommendations.
- [ ] Caveats do not bury the primary actionable answer.
- [ ] Added workflow steps have explicit quality/safety value.

## Exceptions

- User can request maximal rigor for any stake level.
- Regulated/legal/medical/financial requests default one level higher rigor unless clearly educational.

## Release gate

Block if workflow depth is clearly below required rigor for stated stakes, or output is overloaded with non-actionable process detail.
