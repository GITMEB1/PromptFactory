# Prompt Factory v2

Prompt Factory v2 is a **context-and-evidence operating system** for building reliable, auditable LLM outputs in dynamic environments.

## Value proposition

Prompt Factory shifts teams from ad-hoc prompting to a repeatable operating model that:
- improves factual reliability through explicit source-class routing
- reduces hallucination risk with claim-level evidence checks
- supports both fast answers and high-assurance deliverables
- creates a reusable audit trail across tasks, runs, and reviews

Use this repository when you need **traceable, defensible AI outputs** rather than one-off prompt experiments.

## Architecture map

The system is organized as a workflow stack:

1. **Intake & Planning**
   - `task.md`
   - `operating_model.md`
2. **Prompt Execution Layer**
   - `prompts/*.md`
3. **Policy & Governance Layer**
   - `rules/*.md`
4. **Source-Class Layer**
   - `sources/*/source_index.md`
5. **Tracking & Audit Layer**
   - `tracking/*`
6. **Examples & Pattern Library**
   - `examples/*`

For a file-level view, see [`REPO_MAP.md`](./REPO_MAP.md).

## Quickstart links

- Start here: [`QUICKSTART.md`](./QUICKSTART.md)
- Intake specification: [`task.md`](./task.md)
- Workflow and decision model: [`operating_model.md`](./operating_model.md)
- Full manifest and canonical chain: [`MANIFEST.md`](./MANIFEST.md)
- Canonical workflow schemas: [`schemas/`](./schemas)

## Workflow modes

Prompt Factory supports two practical operating modes:

- **Lightweight mode** (speed-biased)
  - Minimal evidence set
  - Short reasoning chain
  - Best for low-risk, low-volatility tasks
- **Deep mode** (assurance-biased)
  - Explicit claim inventory and cross-source validation
  - Formal decision gates and escalation checks
  - Best for high-risk, high-freshness, or externally visible outputs

Mode selection guidance is defined in [`operating_model.md`](./operating_model.md).

## Source-class model

Prompt Factory routes information through five classes:

1. **Official** — standards, docs, primary authoritative references
2. **Practitioner** — implementation guidance, field reports, case studies
3. **Private Context** — user-provided and project-local truth
4. **Live Retrieval** — recency-sensitive web or API evidence
5. **Model Prior** — model prior knowledge, used only when bounded and disclosed

Routing and precedence details live in [`rules/source_routing.md`](./rules/source_routing.md) and [`operating_model.md`](./operating_model.md).

## Constraints

Prompt Factory is designed with explicit constraints:

- no hidden source mixing for high-risk claims
- no confidence without cited evidence
- no silent conflict suppression when sources disagree
- no stale assumptions for freshness-sensitive tasks
- no bypass of policy gates for safety- or compliance-critical work

See [`CHANGE_POLICY.md`](./CHANGE_POLICY.md) and [`DESIGN_PRINCIPLES.md`](./DESIGN_PRINCIPLES.md) for governance constraints.

## Additional repository docs

- [`REPO_MAP.md`](./REPO_MAP.md)
- [`.agent/memory.md`](./.agent/memory.md)
- [`.agent/changelog.md`](./.agent/changelog.md)
- [`.agent/execution_state.md`](./.agent/execution_state.md)
- [`.agent/workflows/default_workflow.md`](./.agent/workflows/default_workflow.md)
- [`DESIGN_PRINCIPLES.md`](./DESIGN_PRINCIPLES.md)
- [`GLOSSARY.md`](./GLOSSARY.md)
- [`CONTRIBUTING.md`](./CONTRIBUTING.md)
- [`CHANGE_POLICY.md`](./CHANGE_POLICY.md)
