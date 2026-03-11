# Repository Map

## Root files

- `README.md` — repository entrypoint that routes operators to the canonical execution spine
- `CANONICAL_EXECUTION_PATH.md` — **primary operator execution path** (authoritative stage/rule/prompt/artifact mapping)
- `operating_model.md` — conceptual model and policy anchors
- `QUICKSTART.md` — fast onboarding aligned to the canonical execution path
- `USAGE_BY_INTERFACE.md` — usage guidance by interface type
- `MANIFEST.md` — inventory and ownership table
- `task.md` — task intake template
- `DESIGN_PRINCIPLES.md` — design principles
- `CHANGE_POLICY.md` — change-control policy
- `CONTRIBUTING.md` — contribution guidance
- `GLOSSARY.md` — glossary of terms

## Directories

- `prompts/` — prompt modules referenced by the canonical execution path
- `rules/` — policy modules
  - **Canonical rule files:** `source_discipline.md`, `claim_safety.md`, `conflict_and_uncertainty.md`, `evaluation_gates.md`, `proportionality.md`
  - **Deprecated/legacy index (reference only):** `DEPRECATIONS.md`
- `sources/` — source-model documents and templates
- `schemas/` — schema templates and examples
- `tracking/` — run and review logs
- `.agent/` — agent memory and execution files
