# Conflict and Uncertainty

Operational controls for conflict adjudication and confidence calibration.

## A) Conflict detection and classification

When sources disagree, classify first:

| Conflict type | Primary check |
|---|---|
| Factual discrepancy | Same metric/event, different value or state |
| Definitional mismatch | Different term definitions/measurement boundaries |
| Timeframe mismatch | Different "as of" dates |
| Scope/jurisdiction mismatch | Different region, system, or applicability |
| Method divergence | Different data collection/analysis methods |

## B) Adjudication sequence

Execute in order:
1. Normalize definitions, units, and time anchors.
2. Compare scope/jurisdiction/version alignment.
3. Weigh credibility and methodological strength.
4. Prefer recency only when topic volatility justifies it.
5. If unresolved, preserve competing views and decision conditions.

## C) Confidence calibration

| Evidence state | Confidence band | Output rule |
|---|---|---|
| Strong agreement, high-quality evidence | High | Direct recommendation allowed |
| Partial agreement or moderate evidence gaps | Medium | Recommendation with caveats/assumptions |
| Material unresolved conflict or thin evidence | Low | Conditional guidance + explicit verification steps |

## D) Uncertainty expression checklist

- [ ] Distinguish facts vs inference vs assumptions.
- [ ] Avoid unsupported precision.
- [ ] Use bounded language when evidence is incomplete.
- [ ] Include next verification action when uncertainty affects decision quality.

## E) Release gate

Block release if any item fails:
- [ ] Material conflict exists but is undisclosed.
- [ ] Confidence label is inconsistent with conflict severity.
- [ ] Single definitive claim presented where evidence is conditionally true by context.
