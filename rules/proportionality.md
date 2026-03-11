# Proportionality

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
