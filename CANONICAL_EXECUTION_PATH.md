# Canonical Execution Path

This document is the authoritative execution source for running Prompt Factory workflows end-to-end.

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

## 3) Stage-by-stage workflow

Canonical stage order:

1. Task Intake
2. Freshness Check
3. Source Routing
4. Retrieval / Reading
5. Credibility Grading
6. Claim Control (Claim Inventory)
7. Response Plan
8. Composition
9. Evaluation (Lint / Eval)
10. Lessons

### Stage details

#### 1. Task Intake
- **Rules consulted:** `rules/proportionality.md`
- **Prompt module:** `prompts/task_intake.md`
- **Artifact emitted:** `schemas/task_intel.md`
- **Gate:** Stop if required task fields, risk, or freshness are missing.

#### 2. Freshness Check
- **Rules consulted:** `rules/source_discipline.md`
- **Prompt module:** `prompts/freshness_checker.md`
- **Artifact emitted:** `schemas/source_bundle.md` (freshness requirements + planned source classes)
- **Gate:** Stop/escalate if freshness requirement cannot be met with current evidence recency.

#### 3. Source Routing
- **Rules consulted:** `rules/source_discipline.md`
- **Prompt module:** `prompts/source_router.md`
- **Artifact emitted:** `schemas/source_bundle.md`
- **Gate:** Stop if any material claim lacks an assigned source class.

#### 4. Retrieval / Reading
- **Rules consulted:** `rules/source_discipline.md`
- **Prompt module:** `prompts/retrieval_reader.md`
- **Artifact emitted:** `schemas/source_record.md`
- **Gate:** Stop if mandatory sources are unavailable, stale, or uncitable.

#### 5. Credibility Grading
- **Rules consulted:** `rules/source_discipline.md`, `rules/conflict_and_uncertainty.md`
- **Prompt module:** `prompts/practitioner_synthesizer.md`
- **Artifact emitted:** `schemas/source_record.md` (credibility/provenance fields populated)
- **Gate:** Escalate if authority is insufficient for decision-critical claims.

#### 6. Claim Control (Claim Inventory)
- **Rules consulted:** `rules/claim_safety.md`, `rules/conflict_and_uncertainty.md`
- **Prompt module:** `prompts/claim_builder.md`
- **Artifact emitted:** `schemas/claim_inventory.md`
- **Gate:** Stop if claims are unsupported, overconfident, or conflict-unresolved.

#### 7. Response Plan
- **Rules consulted:** `rules/proportionality.md`, `rules/claim_safety.md`
- **Prompt module:** `prompts/final_response_builder.md`
- **Artifact emitted:** `schemas/response_plan.md`
- **Gate:** Stop if sections introduce unmapped claims or omit required caveats.

#### 8. Composition
- **Rules consulted:** `rules/claim_safety.md`, `rules/proportionality.md`
- **Prompt module:** `prompts/final_response_builder.md`, `prompts/uncertainty_writer.md`
- **Artifact emitted:** `schemas/delta_record.md` (when revisions occur after drafting)
- **Gate:** Stop if draft contains claims not present in `claim_inventory`.

#### 9. Evaluation (Lint / Eval)
- **Rules consulted:** `rules/evaluation_gates.md`, `rules/claim_safety.md`
- **Prompt module:** `prompts/evaluator.md`, `prompts/critic.md`
- **Artifact emitted:** `schemas/eval_record.md` (+ `schemas/approval_manifest.md` for high-risk release, `schemas/source_conflict_record.md` when conflicts persist)
- **Gate:** Block release on failed policy/evidence checks.

#### 10. Lessons
- **Rules consulted:** `rules/evaluation_gates.md`
- **Prompt module:** `prompts/critic.md`
- **Artifact emitted:** `schemas/lesson_record.md`
- **Gate:** Stop run closure until lessons and failure patterns are logged.

## 4) Rules consulted per stage

Use the stage details above as the fixed map; do not skip rule checks for a stage even in lightweight mode.

## 5) Prompt module invoked per stage

Use exactly the modules listed in each stage unless a deeper escalation adds checks; escalation may add modules, not remove required ones.

## 6) Artifact emitted per stage (`schemas/*`)

Each stage must emit or update at least one schema artifact from `schemas/*` exactly as mapped above.

## 7) Stop gates and escalation triggers

Stop immediately and escalate when any of the following occur:
- Missing intake/risk/freshness classification.
- Mode/evidence mismatch against risk bar.
- Missing source class assignment for a material claim.
- Stale, uncitable, or conflicting evidence on decision-critical claims.
- Evaluator fail after remediation attempt.

Escalation ladder:
1. Lightweight → Deep.
2. Deep → Human review/sign-off.

## 8) Done criteria

A run is done only when all are true:
- All ten stages executed in order (no skipped gates).
- Required schema artifacts are emitted/updated.
- Evaluation passes required risk-level gate.
- Any high-risk release has an `approval_manifest`.
- Lessons are logged for future runs.

## One-screen flow table

| Stage | Rule(s) | Prompt module | Artifact | Gate |
|---|---|---|---|---|
| Task Intake | `rules/proportionality.md` | `prompts/task_intake.md` | `schemas/task_intel.md` | Required fields complete |
| Freshness Check | `rules/source_discipline.md` | `prompts/freshness_checker.md` | `schemas/source_bundle.md` | Evidence recency sufficient |
| Source Routing | `rules/source_discipline.md` | `prompts/source_router.md` | `schemas/source_bundle.md` | Every material claim routed |
| Retrieval / Reading | `rules/source_discipline.md` | `prompts/retrieval_reader.md` | `schemas/source_record.md` | Mandatory sources available/citable |
| Credibility Grading | `rules/source_discipline.md`; `rules/conflict_and_uncertainty.md` | `prompts/practitioner_synthesizer.md` | `schemas/source_record.md` | Authority adequate for critical claims |
| Claim Control | `rules/claim_safety.md`; `rules/conflict_and_uncertainty.md` | `prompts/claim_builder.md` | `schemas/claim_inventory.md` | Claims supported + uncertainty explicit |
| Response Plan | `rules/proportionality.md`; `rules/claim_safety.md` | `prompts/final_response_builder.md` | `schemas/response_plan.md` | No unmapped claims in plan |
| Composition | `rules/claim_safety.md`; `rules/proportionality.md` | `prompts/final_response_builder.md`; `prompts/uncertainty_writer.md` | `schemas/delta_record.md` | Draft remains claim-bound |
| Evaluation | `rules/evaluation_gates.md`; `rules/claim_safety.md` | `prompts/evaluator.md`; `prompts/critic.md` | `schemas/eval_record.md`; `schemas/approval_manifest.md`; `schemas/source_conflict_record.md` | Release blocked on fail |
| Lessons | `rules/evaluation_gates.md` | `prompts/critic.md` | `schemas/lesson_record.md` | Run closure requires logging |
