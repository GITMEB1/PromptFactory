# How to Use Prompt Factory with ChatGPT Attachments

Use this when operating through ChatGPT with uploaded files instead of direct repository access.

## Attachment strategy

Upload, at minimum:
- `task.md`
- `operating_model.md`
- relevant `prompts/*.md`
- relevant `rules/*.md`
- schema templates in `schemas/`
- tracking templates in `tracking/`

Then instruct ChatGPT to return schema-compatible YAML/Markdown blocks that you can paste back into the repository.

## Walkthrough 1 — Lightweight path (low-stakes, low-freshness)

1. Attach core docs + stable context files.
2. Request `task_intel` (`workflow_mode: lightweight`) and a compact `source_bundle`.
3. Request final response with explicit uncertainty notes.
4. Paste artifacts into local files and log task/run entries in `tracking`.

## Walkthrough 2 — Deep path (high-stakes, high-freshness + source conflicts)

1. Attach newest official docs, recency-sensitive evidence, and private context.
2. Require `task_intel` (`workflow_mode: deep`) plus claim-level mapping.
3. If sources disagree, require `source_conflict_record` output with adjudication rationale.
4. Require an approval-ready response plan and evaluator-ready verification summary.
5. Paste results into repo and append run/conflict tracking entries.

## Common failure and recovery

- **Failure: Missing attachment leads to fabricated assumptions.**
  - **Recovery:** Re-run with explicit “only use attached files” and include missing authoritative docs.
- **Failure: Outdated attachment used for high-freshness claim.**
  - **Recovery:** Replace with latest source and redo freshness check + affected claims.
- **Failure: Conflict-handling omitted in generated output.**
  - **Recovery:** Prompt specifically for `source_conflict_record` and block finalization until complete.
- **Failure: Returned format not paste-ready.**
  - **Recovery:** Request strict fenced YAML/Markdown matching schema template keys exactly.
