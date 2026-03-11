# Contributing

> **Contributor mechanics only:** this document covers how to contribute (branching, review checklist, commit expectations). It does not redefine doctrine or behavioral gate policy.

## Branching

- Create a focused branch per change set (for example: `docs/<topic>` or `chore/<topic>`).
- Keep each branch scoped to one reviewable objective.
- Rebase or merge `main` before opening a PR to minimize drift.

## Pull request mechanics

1. Keep changes small and reviewable.
2. Summarize scope and intent clearly in the PR description.
3. Note changed files and why they were touched.
4. Call out potential follow-ups explicitly.

## Commit expectations

- Use clear, imperative commit subjects.
- Keep commits logically grouped; avoid unrelated edits in the same commit.
- Reference impacted docs/rules in the commit body when helpful.

## Review checklist

- [ ] Change is scoped and explained.
- [ ] Any required review/escalation was applied per `CHANGE_POLICY.md`.
- [ ] Canonical docs are linked instead of duplicating policy/doctrine text.
- [ ] Top-level index docs were updated when required.

## Canonical links
- Doctrine and non-negotiable principles: [`DESIGN_PRINCIPLES.md`](DESIGN_PRINCIPLES.md)
- Behavioral gates and escalation requirements: [`CHANGE_POLICY.md`](CHANGE_POLICY.md)
