# Agent Memory

## Purpose
Persistent, high-signal context for recurring work in this repository.

## Ownership
- **Primary owner:** Active execution agent for the current task.
- **Steward:** Repository maintainers review for relevance and drift during periodic cleanup.

## Update cadence
- **Per task start:** Read for prior constraints, assumptions, and open threads.
- **Per major decision:** Append only durable context that should survive the current run.
- **Per task close:** Prune stale or task-specific notes that belong in `execution_state.md` instead.
- **Periodic (maintainer):** Monthly cleanup to remove outdated entries.

## What belongs here
- Stable repository conventions discovered during execution.
- Reusable lessons that improve future task quality or speed.
- Long-lived caveats that are not already documented elsewhere.

## What does not belong here
- Step-by-step progress logs (use `execution_state.md`).
- Historical change records (use `changelog.md`).
- Spec decisions that should live in source docs (update canonical files directly).
