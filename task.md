# Task Intake Specification

Use this file to define the current task before running the workflow.

## Required fields

### 1) Task title
- A concise identifier for the work item.

### 2) User request (verbatim)
- Exact user instruction text.

### 3) Objective statement
- The true outcome the user needs, not just requested format.

### 4) Audience
- Primary reader or decision-maker for the final output.

### 5) Deliverable type
- Examples: answer, plan, policy draft, technical spec, code patch, analysis memo.

### 6) Risk level
- `Low` / `Medium` / `High`.

### 7) Freshness requirement
- `Stable` / `Moderate` / `High`.

### 8) Workflow mode
- `Lightweight` / `Deep`.

### 9) Scope boundaries
- In-scope and out-of-scope items.

### 10) Source constraints
- Required source classes, prohibited sources, citation constraints.

### 11) Success definition
- What “done” means for this task.

## Optional fields

- Stakeholders and approvers
- Known assumptions
- Dependencies and blockers
- Deadline or SLA
- Formatting requirements
- Tone/style requirements
- Compliance requirements
- Privacy constraints
- Tooling constraints
- Prior artifacts or related task IDs

## Acceptance criteria

A task intake is considered valid when all conditions are true:

1. Required fields are complete and unambiguous.
2. Risk and freshness classifications are justified.
3. Workflow mode aligns with risk and evidence requirements.
4. Scope boundaries are explicit enough to prevent hidden work.
5. Success definition is testable (objective pass/fail checks).

## Intake template

```md
Task title:
User request (verbatim):
Objective statement:
Audience:
Deliverable type:
Risk level:
Freshness requirement:
Workflow mode:
Scope boundaries:
Source constraints:
Success definition:

Optional:
- Stakeholders/approvers:
- Assumptions:
- Dependencies/blockers:
- Deadline/SLA:
- Formatting/tone:
- Compliance/privacy:
- Related artifacts:
```
