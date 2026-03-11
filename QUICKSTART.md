# Quickstart

## 1) Read orientation docs

1. [`README.md`](./README.md)
2. [`operating_model.md`](./operating_model.md)
3. [`task.md`](./task.md)

## 2) Create intake

Fill `task.md` using the intake template and required fields.

## 3) Pick execution mode

- Use **Lightweight** for low-risk, low-freshness tasks.
- Use **Deep** for medium/high risk or freshness-sensitive tasks.

## 4) Run the canonical chain

**Task Intake → Freshness Check → Source Routing → Retrieval / Reading → Credibility Grading → Claim Inventory → Response Plan → Composition → Lint / Eval → Lessons**

Use prompt templates in `prompts/` and policy files in `rules/`.

## 5) Log outcomes

Record task outcomes and conflicts in `tracking/` files.

## 6) Improve continuously

Review examples in `examples/` and feed lessons into prompts/rules under `CHANGE_POLICY.md`.

## 7) Use schema artifacts for consistency

Use templates in `schemas/` to make handoffs explicit:
- intake: `task_intel`
- sourcing: `source_record`, `source_bundle`
- synthesis/planning: `claim_inventory`, `response_plan`
- verification/approval: `eval_record`, `approval_manifest`, `source_conflict_record`
- iteration/learning: `delta_record`, `lesson_record`
