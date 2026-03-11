# Evaluation Iteration Workflow

## When to use
Use when improving prompts, policies, or outputs through repeated evaluation cycles and measurable deltas.

## Inputs
- Baseline artifact and target metrics
- Evaluation rubric/test set
- Iteration budget (time/runs)

## Sequence
1. Define metrics, pass thresholds, and stop conditions.
2. Run baseline evaluation and capture diagnostics.
3. Propose one bounded change per iteration.
4. Re-evaluate and compare deltas vs. baseline.
5. Keep, revert, or branch based on measured impact.

## Outputs
- Iteration log with metric deltas
- Best-known configuration and rationale
- Remaining improvement opportunities

## Failure conditions
- Metrics are unstable or non-actionable.
- Changes are not isolated, preventing attribution.
- Iteration budget exhausted before threshold is met.

## Handoff
Share current best state, supporting evaluation data, and prioritized next experiments.
