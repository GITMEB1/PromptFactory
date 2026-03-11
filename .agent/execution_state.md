# Agent Execution State

## Purpose
Current-run operational state for handoffs, resumability, and debugging.

## Ownership
- **Primary owner:** Active execution agent for the current session.
- **Steward:** Next agent in handoff chain confirms and refreshes state before continuing.

## Update cadence
- **At task intake:** Record objective, constraints, and initial plan.
- **After each milestone:** Update status, blockers, and next actions.
- **Before handoff or close:** Ensure state is current and actionable.
- **At task completion:** Mark closed and summarize unresolved follow-ups.

## Suggested sections
- Objective
- Current status
- Completed steps
- In-progress step
- Blockers/risks
- Next actions
- Handoff notes

## Retention
Keep only active or recently relevant context; move long-term learnings to `memory.md` and historical summaries to `changelog.md`.
