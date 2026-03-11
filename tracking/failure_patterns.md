# Failure Patterns

Catalog recurring anti-patterns to catch during intake and evaluation.

## Pattern Template

### FP-XXX — Pattern Name
- **Signal:** Observable symptom in draft/output.
- **Likely Root Cause:** Why it happens.
- **Detection Point:** Intake / Routing / Claims / Output / Eval.
- **Guardrail:** Rule or module to apply.
- **Recovery Playbook:** Steps to remediate in current run.
- **Related Example(s):** `examples/bad/example.md`

---

### FP-001 — Single-Class Source Overreliance
- **Signal:** All major claims cite only one source class (usually practitioner or model prior).
- **Likely Root Cause:** Skipped `source_router` balancing; speed over rigor.
- **Detection Point:** Routing and claim inventory review.
- **Guardrail:** Enforce class coverage from `rules/source_routing.md`.
- **Recovery Playbook:** Add at least one official source for normative claims and one practitioner source for implementation nuance.
- **Related Example(s):** `examples/bad/example.md`

### FP-002 — Hidden Staleness
- **Signal:** Sources older than policy window used without explicit caveat.
- **Likely Root Cause:** Freshness check skipped or only done for one source class.
- **Detection Point:** Freshness checker and eval.
- **Guardrail:** Apply `rules/freshness_policy.md` + `prompts/freshness_checker.md` before composition.
- **Recovery Playbook:** Re-score claim confidence, disclose stale points, and prefer newer replacements.
- **Related Example(s):** `examples/edge_cases/example.md`

### FP-003 — Premature Certainty Under Conflict
- **Signal:** Output presents a single definitive answer despite unresolved source disagreement.
- **Likely Root Cause:** Conflict resolver not invoked; contradictions flattened.
- **Detection Point:** Claim-building and final assembly.
- **Guardrail:** Route through `prompts/source_conflict_resolver.md` and `rules/conflict_resolution.md`.
- **Recovery Playbook:** Surface conflict explicitly, state preferred interpretation, and include a decision rationale.
- **Related Example(s):** `examples/edge_cases/example.md`
