# Change Policy

> **Behavioral gate policy only:** this document defines what changes require review or escalation. It does not restate doctrine or contributor workflow mechanics.

## Change classes

### Patch changes
- Typo corrections, formatting updates, wording clarifications
- No workflow or policy semantics altered

### Minor changes
- Additive docs, new examples, non-breaking prompt guidance
- Existing required gates and constraints remain intact

### Major changes
- Modifies lifecycle stages, decision gates, source precedence, or minimum evidence bars
- Requires explicit review and operator communication

## Mandatory controls

- Any change that lowers evidence thresholds must be justified in writing.
- Any change affecting high-risk workflows requires human operator review.
- Conflicts between docs must be resolved before merge.
- README and REPO_MAP should be updated when adding top-level docs.

## Review triggers

Require elevated review when a change touches:
- `operating_model.md`
- `rules/*.md`
- `prompts/*.md` with policy impact

## Backward compatibility intent

Prefer additive changes. If behavioral breaking changes are necessary, mark them clearly as major and provide migration guidance in the PR description.

## Canonical links
- Enduring doctrine and rationale: [`DESIGN_PRINCIPLES.md`](DESIGN_PRINCIPLES.md)
- Contributor branching/checklist/commit mechanics: [`CONTRIBUTING.md`](CONTRIBUTING.md)
