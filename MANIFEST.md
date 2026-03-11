# Prompt Factory Manifest

## Inventory + ownership

| Path | Purpose | Owner |
|---|---|---|
| `README.md` | Repository entrypoint that sends operators to the canonical execution path | Core maintainers |
| `CANONICAL_EXECUTION_PATH.md` | Canonical stage-by-stage execution spine (rules, prompts, artifacts, gates) | Core maintainers |
| `operating_model.md` | Canonical concept definitions and policy anchors | Core maintainers |
| `QUICKSTART.md` | Operator onboarding using direct canonical-path workflow | Core maintainers |
| `REPO_MAP.md` | Structural map of repository paths and canonical/deprecated markers | Core maintainers |
| `USAGE_BY_INTERFACE.md` | Interface-specific usage notes with shared workflow core | Core maintainers |
| `task.md` | Structured intake specification | Operators |
| `prompts/task_intake.md` | Canonical task intake prompt module | Prompt maintainers |
| `prompts/freshness_checker.md` | Canonical freshness-check prompt module | Prompt maintainers |
| `prompts/source_router.md` | Canonical source-routing prompt module | Prompt maintainers |
| `prompts/retrieval_reader.md` | Canonical retrieval/reading prompt module | Prompt maintainers |
| `prompts/practitioner_synthesizer.md` | Canonical credibility-grading prompt module | Prompt maintainers |
| `prompts/claim_builder.md` | Canonical claim-control prompt module | Prompt maintainers |
| `prompts/final_response_builder.md` | Canonical response-plan prompt module | Prompt maintainers |
| `prompts/uncertainty_writer.md` | Canonical composition prompt module | Prompt maintainers |
| `prompts/evaluator.md` | Canonical evaluation prompt module | Prompt maintainers |
| `prompts/critic.md` | Canonical lessons prompt module | Prompt maintainers |
| `prompts/lightweight_mode.md` | Mode interface prompt for lightweight runs | Prompt maintainers |
| `prompts/deep_mode.md` | Mode interface prompt for deep runs | Prompt maintainers |
| `rules/source_discipline.md` | Canonical source routing, credibility, and freshness controls | Policy maintainers |
| `rules/claim_safety.md` | Canonical claim safety and provenance controls | Policy maintainers |
| `rules/conflict_and_uncertainty.md` | Canonical conflict adjudication and uncertainty calibration | Policy maintainers |
| `rules/evaluation_gates.md` | Canonical evaluation and release-gate criteria | Policy maintainers |
| `rules/proportionality.md` | Canonical proportionality and rigor-sizing policy | Policy maintainers |
| `rules/DEPRECATIONS.md` | Legacy-to-canonical mapping index (deprecated reference only) | Policy maintainers |
| `sources/*.md` | Source-model references and templates | Research maintainers |
| `schemas/*.md` | Canonical workflow artifact schemas | Schema maintainers |
| `tracking/*.md` | Task/run/eval/conflict/lesson logs | Operators |
| `.agent/*.md` | Agent memory and execution state docs | Automation maintainers |

## Final retained canonical rule set

- `rules/source_discipline.md`
- `rules/claim_safety.md`
- `rules/conflict_and_uncertainty.md`
- `rules/evaluation_gates.md`
- `rules/proportionality.md`

## Final retained canonical prompt modules

- `prompts/task_intake.md`
- `prompts/freshness_checker.md`
- `prompts/source_router.md`
- `prompts/retrieval_reader.md`
- `prompts/practitioner_synthesizer.md`
- `prompts/claim_builder.md`
- `prompts/final_response_builder.md`
- `prompts/uncertainty_writer.md`
- `prompts/evaluator.md`
- `prompts/critic.md`
- `prompts/lightweight_mode.md`
- `prompts/deep_mode.md`

## Concept owner table

| Concept | Owner file |
|---|---|
| Prompt engineering | [`operating_model.md#prompt-engineering`](./operating_model.md#prompt-engineering) |
| Context engineering | [`operating_model.md#context-engineering`](./operating_model.md#context-engineering) |
| Source routing | [`operating_model.md#source-routing`](./operating_model.md#source-routing) |
| Retrieval | [`operating_model.md#retrieval`](./operating_model.md#retrieval) |
| Grounding | [`operating_model.md#grounding`](./operating_model.md#grounding) |
| Claim control | [`operating_model.md#claim-control`](./operating_model.md#claim-control) |
| Composition | [`operating_model.md#composition`](./operating_model.md#composition) |
| Evaluation | [`operating_model.md#evaluation`](./operating_model.md#evaluation) |
| Lessons | [`operating_model.md#lessons`](./operating_model.md#lessons) |
