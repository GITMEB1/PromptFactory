# Source Selection Matrix

Use this matrix to choose the **minimum required source bundle** by task type, risk, and freshness sensitivity.

| Task Type | Risk Level | Freshness Need | Required Source Bundle | Notes |
|---|---|---|---|---|
| Concept explanation / background | Low | Low | `model_prior + official (optional)` | Official is recommended when terminology is contested. |
| How-to implementation guidance | Medium | Medium | `official + practitioner` | Add retrieval if versions/releases may have changed recently. |
| Environment-specific troubleshooting | Medium-High | Medium | `private_context + official + practitioner` | Prefer private context as constraint anchor. |
| Policy/compliance interpretation | High | Medium-High | `official + private_context + retrieval` | Practitioner can supplement but not replace official basis. |
| Time-sensitive operational decision | High | High | `retrieval + official + private_context` | Retrieval must include run timestamp and at least 2 corroborating sources when possible. |
| Vendor/version comparison | Medium-High | High | `retrieval + official + practitioner` | Require retrieval for pricing/features that drift frequently. |
| Incident/outage response narrative | High | High | `private_context + retrieval + official` | Use official status pages plus internal telemetry/log context. |

## Escalation Rules
- If **risk is High**, include at least one authoritative source class (`official` or `private_context`) plus retrieval when stale risk is Medium or High.
- If **freshness need is High**, retrieval is mandatory regardless of task type.
- If only model prior is available for a medium/high-risk task, output must be downgraded to hypotheses with explicit verification gaps.
