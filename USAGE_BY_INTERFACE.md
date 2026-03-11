# Usage by Interface

## Common workflow core

All interfaces use the same operating loop:
1. Create `task_intel` from `task.md`.
2. Run the canonical chain (intake → freshness → routing → sourcing → claims → plan → composition → eval).
3. Produce schema-compatible artifacts from `schemas/`.
4. Log outcomes in `tracking/`.

## Codex (repo-aware)

Use when the assistant can directly inspect/edit repository files.

- Ask for staged artifacts first, final answer last.
- Require claim-level evidence mapping for deep mode.
- Ensure commits and tracking entries reference produced artifacts.

## Generic LLM chat/API

Use when the model cannot directly access the repository.

- Paste required context from `task.md`, `rules/`, `prompts/`, and relevant source files.
- Require strict YAML/Markdown outputs aligned to `schemas/` keys.
- Re-run prompts when structure, citations, or conflict adjudication are incomplete.

## ChatGPT with attachments

Use when providing context as uploaded files.

- Attach core docs (`task.md`, `operating_model.md`, relevant `prompts/`, `rules/`, `schemas/`, `tracking/`).
- Instruct: “Use only attached files for claims; disclose uncertainty when evidence is missing.”
- Paste model outputs back into repository artifacts and tracking logs.
