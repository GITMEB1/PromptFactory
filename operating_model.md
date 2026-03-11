# Operating Model

## Purpose

Prompt Factory treats prompting as a **workflow and knowledge-governance problem**, not just a wording problem.

## Canonical concept definition source

`operating_model.md` is the canonical source for concept definitions used across this repository.

## Canonical execution mapping source

For all procedural stage execution (order, mapped rules, prompt modules, schema outputs, and stop gates), use [`CANONICAL_EXECUTION_PATH.md`](./CANONICAL_EXECUTION_PATH.md) as the single operational source of truth. This file intentionally focuses on concepts and policy anchors.

## Canonical concept definitions

### Prompt engineering

Designing module instructions so model behavior is predictable and auditable.

**In scope:** Prompt interfaces, procedure steps, outputs, quality checks.
**Out of scope / non-goals:** Treating wording tweaks as a replacement for sourcing, provenance, or evaluation controls.

### Context engineering

Structuring task constraints, source artifacts, and workflow state so the model receives the right information at the right step.

**In scope:** Task intel, source bundles, claim inventory, response plans, mode/risk controls.
**Out of scope / non-goals:** Blindly expanding context window without relevance or provenance discipline.

### Source routing

Assigning each material claim to required source classes based on risk, freshness, and authority needs.

**In scope:** Routing policies, source-class selection rationale, escalation to retrieval.
**Out of scope / non-goals:** Convenience-first sourcing for high-risk claims.

### Retrieval

Acquiring evidence from external or indexed systems to satisfy routed source requirements, especially freshness-sensitive claims.

**In scope:** Retrieval plans, timestamped evidence capture, reruns when stale.
**Out of scope / non-goals:** Assuming retrieved snippets are trustworthy without credibility/provenance checks.

### Grounding

Binding output claims to explicit, traceable evidence and clear uncertainty language when evidence is incomplete.

**In scope:** Claim-to-source linkage, caveats, conflict visibility.
**Out of scope / non-goals:** Unsupported factual assertions and implicit confidence inflation.

### Claim control

Managing the lifecycle of material claims: include, revise, defer, or exclude based on support quality.

**In scope:** Claim inventory, approval/exclusion decisions, change tracking.
**Out of scope / non-goals:** Freeform drafting that introduces unmapped claims.

### Composition

Assembling approved claims into a user-facing response that preserves intent, structure, and uncertainty disclosures.

**In scope:** Section planning, claim rebinding, final formatting.
**Out of scope / non-goals:** Adding new factual content not cleared by claim control.

### Evaluation

Systematic post-draft assessment of factual and quality dimensions, with release gates and remediation.

**In scope:** Pass/warn/fail scoring, policy checks, confidence scoring, iteration triggers.
**Out of scope / non-goals:** Style-only review that ignores grounding/freshness failures.

### Lessons

Capturing reusable outcomes from runs to improve future routing, prompting, and review decisions.

**In scope:** Lesson logs, failure patterns, exemplars, review notes.
**Out of scope / non-goals:** One-off retrospective notes that are not linked to operational artifacts.

## Escalation conditions

Escalate from lightweight to deep mode, or from deep mode to human review, when any of the following occur:

- high-risk task class (legal, financial, safety, compliance, public commitments)
- source conflicts on decision-critical claims
- freshness requirement exceeds available evidence recency
- insufficient official or private-primary evidence for mandatory claims
- ambiguous user intent with material downstream consequence
- repeated evaluator failures across two iterations

## Minimum evidence requirements by task risk

| Risk level | Minimum evidence bar | Allowed model-prior usage | Required review |
|---|---|---|---|
| Low | At least one plausible source path per material claim; explicit caveats allowed | Allowed for non-critical background with disclosure | Self-check |
| Medium | Two independent supports for key claims, including at least one non-prior source | Limited to gap-filling; must not anchor final critical claims | Peer or evaluator pass |
| High | Strong, preference-ranked evidence with authoritative support for all critical claims; conflicts documented | Not allowed as sole basis for critical claims | Human operator sign-off |

## Source precedence

- For unstable facts: **Official + Live Retrieval** outrank everything else.
- For user/project-local truth: **Private primary context** may outrank outside inference.
- For workflow/process advice: **Practitioner sources** may outperform official docs.
- For current uncertainty: do not rely on model prior alone.
- If sources conflict: show the conflict instead of smoothing it over.
