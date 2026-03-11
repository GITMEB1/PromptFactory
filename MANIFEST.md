# Prompt Factory Manifest

## File-purpose table

| Path | Purpose |
|---|---|
| `README.md` | Repository overview, value proposition, navigation links |
| `QUICKSTART.md` | Fast onboarding path for first execution |
| `MANIFEST.md` | Canonical repository intent and operating assumptions |
| `REPO_MAP.md` | Directory-level map of repository structure |
| `DESIGN_PRINCIPLES.md` | System principles and non-negotiable design choices |
| `CHANGE_POLICY.md` | Rules for modifying prompts, policies, and operating docs |
| `CONTRIBUTING.md` | Contribution workflow and documentation expectations |
| `GLOSSARY.md` | Shared terminology used across the repository |
| `task.md` | Structured task intake specification |
| `operating_model.md` | Lifecycle, decision gates, risk controls, and escalation model |
| `prompts/*.md` | Role-specific prompt templates in the execution chain |
| `rules/*.md` | Policy constraints for routing, credibility, freshness, and conflict handling |
| `sources/*/source_index.md` | Source-class inventories and guidance |
| `tracking/*` | Run logs, evaluation logs, conflicts, and task tracking records |
| `examples/*` | Good/bad/edge examples for operator calibration |

## Canonical workflow chain

**Task Intake → Freshness Check → Source Routing → Retrieval / Reading → Credibility Grading → Claim Inventory → Response Plan → Composition → Lint / Eval → Lessons**

This chain is the default operating path for both human and LLM operators. Steps may be compressed only in low-risk lightweight mode.

## Versioning assumptions

- Repository docs follow **semantic intent versioning**:
  - **Major**: operating-model changes that alter required stages, gates, or source precedence
  - **Minor**: additive guidance, new templates, expanded examples, or clarifications
  - **Patch**: typo fixes, wording improvements, and non-behavioral formatting updates
- Prompt or rule edits that change output behavior should be logged in `tracking/review_log.md`.
- Version labels should be reflected in release notes or commit messages when process semantics change.

## Intended users

### Human operator
- Owns scoping, judgment calls, and approval at decision gates
- Uses this repository to produce auditable AI-assisted outputs
- Resolves ambiguity, compliance constraints, and stakeholder trade-offs

### LLM operator
- Executes prompt roles and workflow stages consistently
- Follows source routing and evidence requirements
- Flags uncertainty, conflicts, and escalation conditions instead of guessing

Both operator types should converge on the same chain, evidence bar, and policy constraints.
