# Prompt Factory Manifest

## Inventory + ownership

| Path | Purpose | Owner |
|---|---|---|
| `README.md` | Repository entrypoint and concept references | Core maintainers |
| `operating_model.md` | Canonical concept definitions, lifecycle, gates, and decision policy | Core maintainers |
| `QUICKSTART.md` | Operator onboarding and first-run examples | Core maintainers |
| `REPO_MAP.md` | Structural map of repository paths | Core maintainers |
| `USAGE_BY_INTERFACE.md` | Interface-specific usage notes with shared workflow core | Core maintainers |
| `task.md` | Structured intake specification | Operators |
| `prompts/*.md` | Execution-stage prompt modules | Prompt maintainers |
| `rules/source_discipline.md` | Canonical source routing, credibility, and freshness controls | Policy maintainers |
| `rules/claim_safety.md` | Canonical claim safety and provenance controls | Policy maintainers |
| `rules/conflict_and_uncertainty.md` | Canonical conflict adjudication and uncertainty calibration | Policy maintainers |
| `rules/evaluation_gates.md` | Canonical evaluation and release-gate criteria | Policy maintainers |
| `rules/proportionality.md` | Canonical proportionality and rigor-sizing policy | Policy maintainers |
| `rules/DEPRECATIONS.md` | Legacy-to-canonical policy mapping index | Policy maintainers |
| `sources/*.md` | Source-model references and templates | Research maintainers |
| `schemas/*.md` | Canonical workflow artifact schemas | Schema maintainers |
| `tracking/*.md` | Task/run/eval/conflict/lesson logs | Operators |
| `.agent/*.md` | Agent memory and execution state docs | Automation maintainers |

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
