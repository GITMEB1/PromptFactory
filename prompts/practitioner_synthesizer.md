# Prompt Module — Practitioner Synthesizer

## When invoked
- When practitioner sources are included and implementation guidance is needed.
- Triggered after extraction but before final composition.
- Requires vetted practitioner evidence and credibility context.

## Inputs
- **Required**
  - Practitioner evidence notes.
  - Credibility assessments for practitioner sources.
  - Task context (environment, constraints, goals).
- **Optional**
  - Official guidance to align or contrast with practitioner advice.
  - User preference for conservative vs experimental recommendations.

## Procedure
1. Cluster practitioner insights by scenario similarity.
2. Separate reproducible patterns from anecdotal one-offs.
3. Cross-check practitioner claims against official/primary sources when available.
4. Extract implementation heuristics, tradeoffs, and failure triggers.
5. Convert validated patterns into actionable recommendations with guardrails.
6. Flag high-variance advice for uncertainty handling.

## Outputs
- `practitioner_synthesis_notes`:
  - pattern
  - applicability_conditions
  - tradeoffs
  - guardrails
  - supporting_sources
- `high_variance_flags`.

## Quality checks
- Anecdotes are not presented as universal truth.
- Applicability conditions are explicit.
- Conflicts with official guidance are surfaced.
- Recommendations include operational guardrails.

## Failure patterns
- **Symptom:** Trend-driven advice treated as established practice.
  - Cause: Credibility and reproducibility checks skipped.
  - Fix: Require pattern validation fields.
- **Symptom:** Good ideas fail in user context.
  - Cause: Applicability conditions omitted.
  - Fix: Add environment constraints per recommendation.
- **Symptom:** Practitioner and official guidance diverge silently.
  - Cause: Cross-check step omitted.
  - Fix: Route divergence to conflict resolver.
