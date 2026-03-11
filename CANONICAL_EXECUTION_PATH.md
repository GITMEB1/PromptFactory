# Canonical Execution Path

This document is the **single source of truth** for workflow-stage execution mapping in Prompt Factory.

## 1) Read order

Read these in order before executing a run:
1. [`README.md`](./README.md)
2. [`QUICKSTART.md`](./QUICKSTART.md)
3. [`operating_model.md`](./operating_model.md)
4. [`task.md`](./task.md)
5. This file: [`CANONICAL_EXECUTION_PATH.md`](./CANONICAL_EXECUTION_PATH.md)

## 2) Mode selection (lightweight vs deep)

Select mode immediately after intake:
- **Lightweight mode** (`prompts/lightweight_mode.md`): low-risk tasks with stable facts and acceptable caveats.
- **Deep mode** (`prompts/deep_mode.md`): medium/high-risk, freshness-sensitive, externally consequential, or conflict-prone tasks.

Mode rules:
- Apply [`operating_model.md#minimum-evidence-requirements-by-task-risk`](./operating_model.md#minimum-evidence-requirements-by-task-risk).
- Apply [`operating_model.md#escalation-conditions`](./operating_model.md#escalation-conditions).
- If any escalation trigger appears during execution, promote to deep mode (or human review if already deep).

## 3) Canonical workflow stage mapping (authoritative)

Use this table as the only canonical mapping between workflow stage, governing rules, prompt module, and schema output.

| Stage | Primary rule file(s) | Primary prompt module | Expected artifact schema output |
|---|---|---|---|
| Task Intake | `rules/proportionality.md` | `prompts/task_intake.md` | `schemas/task_intel.md` |
| Freshness Check | `rules/source_discipline.md` | `prompts/freshness_checker.md` | `schemas/source_bundle.md` |
| Source Routing | `rules/source_discipline.md` | `prompts/source_router.md` | `schemas/source_bundle.md` |
| Retrieval / Reading | `rules/source_discipline.md` | `prompts/retrieval_reader.md` | `schemas/source_record.md` |
| Credibility Grading | `rules/source_discipline.md`; `rules/conflict_and_uncertainty.md` | `prompts/practitioner_synthesizer.md` | `schemas/source_record.md` |
| Claim Control (Claim Inventory) | `rules/claim_safety.md`; `rules/conflict_and_uncertainty.md` | `prompts/claim_builder.md` | `schemas/claim_inventory.md` |
| Response Plan | `rules/proportionality.md`; `rules/claim_safety.md` | `prompts/final_response_builder.md` | `schemas/response_plan.md` |
| Composition | `rules/claim_safety.md`; `rules/proportionality.md` | `prompts/uncertainty_writer.md` | `schemas/delta_record.md` |
| Evaluation (Lint / Eval) | `rules/evaluation_gates.md`; `rules/claim_safety.md` | `prompts/evaluator.md` | `schemas/eval_record.md` |
| Lessons | `rules/evaluation_gates.md` | `prompts/critic.md` | `schemas/lesson_record.md` |

### Stage order

Execute stages in this exact order:

**Task Intake → Freshness Check → Source Routing → Retrieval / Reading → Credibility Grading → Claim Control (Claim Inventory) → Response Plan → Composition → Evaluation (Lint / Eval) → Lessons**

## 4) Current stage self-check

Use this block at any point in a run:

```text
Current stage self-check
- Which workflow am I in?
- Which rule applies now?
- Which prompt is next?
- What artifact am I producing?
```

Answer by reading the current row in the canonical workflow stage mapping table above.

## 5) Stop gates and escalation triggers

Stop immediately and escalate when any of the following occur:
- Missing intake/risk/freshness classification.
- Mode/evidence mismatch against risk bar.
- Missing source class assignment for a material claim.
- Stale, uncitable, or conflicting evidence on decision-critical claims.
- Evaluator fail after remediation attempt.

Escalation ladder:
1. Lightweight → Deep.
2. Deep → Human review/sign-off.

## 6) Done criteria

A run is done only when all are true:
- All ten stages executed in order.
- Required schema artifacts are emitted/updated for each stage.
- Evaluation passes required risk-level gate.
- Any high-risk release has an `approval_manifest`.
- Lessons are logged for future runs.
