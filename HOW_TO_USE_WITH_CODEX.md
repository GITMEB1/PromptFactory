# How to Use Prompt Factory with Codex

Use this when Codex can inspect/edit repo files directly.

## Recommended execution pattern

1. Start with repository intake and create a schema-aligned `task_intel` artifact.
2. Use Codex to read policy + prompt modules and produce intermediate artifacts in schema format.
3. Validate with repository checks (format, consistency, and evaluator prompts).
4. Commit and track results in `tracking/` templates.

## Walkthrough 1 — Lightweight path (low-stakes, low-freshness)

- Ask Codex to:
  - classify risk/freshness as `low/stable`
  - produce lightweight artifacts (`task_intel`, `source_bundle`, `response_plan`)
  - compose final answer with file citations
- Record:
  - `tracking/tasks.yaml.md` with lightweight routing hint
  - `tracking/runs.yaml.md` with minimal module path

## Walkthrough 2 — Deep path (high-stakes, high-freshness + source conflicts)

- Ask Codex to:
  - enforce `workflow_mode: deep`
  - generate claim-level evidence mapping
  - detect and record conflicts using `schemas/source_conflict_record.md`
- Require:
  - conflict-aware response with caveats/disclosures
  - evaluation + approval artifacts for high-risk outputs
- Record:
  - `tracking/source_conflicts.yaml.md`
  - `tracking/runs.yaml.md` with freshness outcomes and escalation flag

## Common failure and recovery

- **Failure: Codex answers directly without staged artifacts.**
  - **Recovery:** Instruct “produce artifacts first, final answer last” and list required schemas explicitly.
- **Failure: Deep tasks not escalated after conflict.**
  - **Recovery:** Enforce gate: unresolved/high-severity conflicts block delivery pending adjudication.
- **Failure: Output includes confidence not backed by evidence.**
  - **Recovery:** Run evaluator prompt and downgrade or remove unsupported claims.
- **Failure: Commit lacks audit trail references.**
  - **Recovery:** Update docs or run notes to point to corresponding tracking entries.
