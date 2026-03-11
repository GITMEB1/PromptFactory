# How to Use Prompt Factory with Any LLM

Use this when you are operating in a generic chat UI or API workflow without repository-aware automation.

## Operator loop

1. Copy intake fields from `task.md` into a `task_intel` artifact.
2. Ask the model to follow the canonical chain:
   - intake → freshness check → routing → sourcing → claim inventory → plan → composition → eval.
3. Require outputs in schema-compatible blocks (`schemas/*.md`).
4. Log task/run/conflict entries in `tracking/*.md` templates.

## Walkthrough 1 — Lightweight path (low-stakes, low-freshness)

- Prompt the model to produce:
  - `task_intel` with `workflow_mode: lightweight`
  - minimal `source_bundle`
  - concise `claim_inventory` and `response_plan`
- Deliver short answer with citations and caveats.
- Update tracking:
  - `tracking/tasks.yaml.md` (`status: done`)
  - `tracking/runs.yaml.md` (`mode: lightweight`)

## Walkthrough 2 — Deep path (high-stakes, high-freshness + source conflicts)

- Prompt the model to produce:
  - `task_intel` with `workflow_mode: deep`
  - full `source_bundle` with class coverage
  - `claim_inventory` for decision-critical claims
- If disagreement appears, require `source_conflict_record` and conflict-aware response plan.
- Gate release on evaluator output + approval manifest for high-risk scenarios.
- Update tracking:
  - `tracking/source_conflicts.yaml.md`
  - `tracking/runs.yaml.md` with freshness check outcome.

## Common failure and recovery

- **Failure: Model skips schema structure.**
  - **Recovery:** Re-prompt with exact schema headings and require valid YAML blocks.
- **Failure: Citations are broad or missing claim linkage.**
  - **Recovery:** Enforce claim IDs and source IDs in `claim_inventory` + `source_bundle`.
- **Failure: Conflict is summarized but not adjudicated.**
  - **Recovery:** Require explicit `resolution_status`, `rationale`, and residual uncertainty in `source_conflict_record`.
- **Failure: Tracking omitted after delivery.**
  - **Recovery:** Add run/task/conflict entries immediately before closing the task.
