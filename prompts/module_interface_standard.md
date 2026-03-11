# Prompt Module Interface Standard

This document defines the required shape for all module documents in `prompts/`.

## Required section order

Each module specification must include the following sections in this order:

1. **When invoked**
2. **Inputs**
3. **Procedure**
4. **Outputs**
5. **Quality checks**
6. **Failure patterns**

## Section requirements

### 1) When invoked
- Describe the exact workflow stage where the module is used.
- State trigger conditions (for example: task risk, freshness sensitivity, mode selection, policy gate).
- State any hard preconditions that must be true before execution.

### 2) Inputs
- List required inputs first, then optional inputs.
- Use explicit names that can be referenced by other modules.
- Include provenance expectations for each input where relevant.

### 3) Procedure
- Define a deterministic, stepwise process.
- Keep steps actionable and auditable.
- Include branch behavior for common variants (for example, lightweight vs deep mode).

### 4) Outputs
- Define concrete artifacts produced by the module.
- Include minimum required fields for each artifact.
- Clarify where outputs are handed off next.

### 5) Quality checks
- Provide pass/fail checks that can be run immediately.
- Prefer objective checks over vague quality language.
- Include escalation criteria when checks fail.

### 6) Failure patterns
- Document recurring failure modes and their observable symptoms.
- State likely causes.
- Provide remediation actions or escalation route.

## Formatting conventions

- Use concise bullets for checklists and artifacts.
- Use numbered lists for procedures.
- Keep module scope narrow: one module should own one responsibility boundary.
- Avoid embedding policy text that already lives in `rules/`; link or reference policy names instead.
- Keep naming consistent with adjacent modules to support composability.
