# Repository Map

## Root files

- `README.md` — overview, architecture, and navigation
- `MANIFEST.md` — file purposes, workflow chain, users, and version assumptions
- `QUICKSTART.md` — fast onboarding sequence
- `operating_model.md` — lifecycle stages, gates, escalation, evidence bars
- `task.md` — structured intake spec
- `DESIGN_PRINCIPLES.md` — design doctrine and non-negotiables
- `GLOSSARY.md` — common vocabulary
- `CONTRIBUTING.md` — contribution expectations and process
- `CHANGE_POLICY.md` — change controls and review thresholds
- `.agent/memory.md` — durable agent memory and long-lived context
- `.agent/changelog.md` — agent-authored change history and validation notes
- `.agent/execution_state.md` — active run state for handoffs and resumability

## Directories

- `prompts/`
  - Role prompts used during execution (intake, routing, claim building, composition, evaluation)
- `rules/`
  - Governance policies for routing, freshness, credibility, composition, and conflict resolution
- `sources/`
  - Source-class indexes:
    - `official/`
    - `practitioner/`
    - `private_context/`
    - `retrieval/`
    - `model_prior/`
- `tracking/`
  - Run/task/review/evaluation/conflict records
- `examples/`
  - Positive, negative, and edge-case examples for calibration
- `.agent/`
  - Agent operational docs and workflow playbooks
  - `workflows/`
    - `default_workflow.md`
    - `research_workflow.md`
    - `writing_workflow.md`
    - `analysis_workflow.md`
    - `review_workflow.md`
    - `source_conflict_workflow.md`
    - `eval_iteration_workflow.md`
- `schemas/`
  - Canonical YAML/Markdown schema templates and filled examples for workflow artifacts
