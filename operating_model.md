# Operating Model

## Purpose

Prompt Factory v2 treats prompting as a **workflow and knowledge-governance problem**, not just a wording problem.

## Concept boundaries (canonical definitions)

These definitions set scope boundaries for the full system. Use these terms consistently across docs, prompts, and logs.

| Concept | Definition | In scope | Out of scope / non-goals |
|---|---|---|---|
| **Prompt engineering** | Designing module instructions so model behavior is predictable and auditable. | Prompt interfaces, procedure steps, outputs, quality checks. | Treating wording tweaks as a replacement for sourcing, provenance, or evaluation controls. |
| **Context engineering** | Structuring task constraints, source artifacts, and workflow state so the model receives the right information at the right step. | Task intel, source bundles, claim inventory, response plans, mode/risk controls. | Blindly expanding context window without relevance or provenance discipline. |
| **Source routing** | Assigning each material claim to required source classes based on risk, freshness, and authority needs. | Routing policies, source-class selection rationale, escalation to retrieval. | Convenience-first sourcing for high-risk claims. |
| **Retrieval** | Acquiring evidence from external or indexed systems to satisfy routed source requirements, especially freshness-sensitive claims. | Retrieval plans, timestamped evidence capture, reruns when stale. | Assuming retrieved snippets are trustworthy without credibility/provenance checks. |
| **Grounding** | Binding output claims to explicit, traceable evidence and clear uncertainty language when evidence is incomplete. | Claim-to-source linkage, caveats, conflict visibility. | Unsupported factual assertions and implicit confidence inflation. |
| **Claim control** | Managing the lifecycle of material claims: include, revise, defer, or exclude based on support quality. | Claim inventory, approval/exclusion decisions, change tracking. | Freeform drafting that introduces unmapped claims. |
| **Composition** | Assembling approved claims into a user-facing response that preserves intent, structure, and uncertainty disclosures. | Section planning, claim rebinding, final formatting. | Adding new factual content not cleared by claim control. |
| **Evaluation** | Systematic post-draft assessment of factual and quality dimensions, with release gates and remediation. | Pass/warn/fail scoring, policy checks, confidence scoring, iteration triggers. | Style-only review that ignores grounding/freshness failures. |
| **Lessons** | Capturing reusable outcomes from runs to improve future routing, prompting, and review decisions. | Lesson logs, failure patterns, exemplars, review notes. | One-off retrospective notes that are not linked to operational artifacts. |

## Lifecycle stages

1. **Intake**
   - Capture task requirements in `task.md`
   - Classify risk, freshness, and deliverable type
2. **Scoping**
   - Select lightweight or deep mode
   - Define acceptable uncertainty and response boundaries
3. **Sourcing**
   - Route required claims to source classes
   - Gather evidence from official, practitioner, private context, retrieval, or bounded model prior
4. **Synthesis**
   - Build claim inventory and response plan
   - Track confidence and unresolved gaps
5. **Verification**
   - Run lint/eval checks and contradiction checks
   - Ensure minimum evidence requirements are met
6. **Delivery**
   - Produce final response with caveats and references
7. **Lessons**
   - Log outcomes, conflicts, and improvements in `tracking/*`

## Decision gates

### Gate A: Intake completeness
Pass conditions:
- required fields in `task.md` are complete
- risk and freshness are classified

Fail action:
- return for clarification before sourcing

### Gate B: Mode selection
Pass conditions:
- mode (lightweight/deep) matches risk and freshness
- operator acknowledges trade-off between speed and assurance

Fail action:
- escalate mode to deep or pause task

### Gate C: Evidence sufficiency
Pass conditions:
- every material claim has a source class and support
- uncertainty is explicit where evidence is incomplete

Fail action:
- block delivery and continue sourcing

### Gate D: Policy compliance
Pass conditions:
- output conforms to routing, freshness, and conflict policies
- no prohibited shortcuts (e.g., silent source substitution)

Fail action:
- reroute through policy remediation before release

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

## Canonical execution chain

**Task Intake → Freshness Check → Source Routing → Retrieval / Reading → Credibility Grading → Claim Control (Claim Inventory) → Response Plan → Composition → Evaluation (Lint / Eval) → Lessons**

## Concept traceability matrix

This table maps each canonical concept to operational artifacts in required directories.

| Concept | `rules/` | `prompts/` | `sources/` | `tracking/` | `.agent/workflows/` |
|---|---|---|---|---|---|
| Prompt engineering | `rules/claim_safety.md` | `prompts/final_response_builder.md` | `sources/source_bundle_template.md` | `tracking/review_log.md` | `.agent/workflows/writing_workflow.md` |
| Context engineering | `rules/claim_safety.md` | `prompts/task_intake.md`; `prompts/claim_builder.md` | `sources/provenance_model.md`; `sources/private_context/source_index.md` | `tracking/tasks.yaml.md`; `tracking/runs.yaml.md` | `.agent/workflows/default_workflow.md` |
| Source routing | `rules/source_discipline.md` | `prompts/source_router.md`; `prompts/freshness_checker.md` | `sources/source_selection_matrix.md`; `sources/official/source_index.md` | `tracking/source_conflicts.yaml.md` | `.agent/workflows/research_workflow.md` |
| Retrieval | `rules/source_discipline.md` | `prompts/retrieval_reader.md`; `prompts/source_conflict_resolver.md` | `sources/retrieval/source_index.md`; `sources/freshness_risk_matrix.md` | `tracking/runs.yaml.md` | `.agent/workflows/research_workflow.md` |
| Grounding | `rules/claim_safety.md`; `rules/conflict_and_uncertainty.md` | `prompts/claim_builder.md`; `prompts/uncertainty_writer.md` | `sources/provenance_model.md`; `sources/model_prior/usage_policy.md` | `tracking/eval_log.yaml.md` | `.agent/workflows/review_workflow.md` |
| Claim control | `rules/claim_safety.md` | `prompts/claim_builder.md`; `prompts/final_response_builder.md` | `sources/source_bundle_template.md` | `tracking/failure_patterns.md`; `tracking/review_log.md` | `.agent/workflows/analysis_workflow.md` |
| Composition | `rules/claim_safety.md`; `rules/proportionality.md` | `prompts/final_response_builder.md` | `sources/source_bundle_template.md` | `tracking/exemplar_index.md` | `.agent/workflows/writing_workflow.md` |
| Evaluation | `rules/evaluation_gates.md` | `prompts/evaluator.md`; `prompts/critic.md` | `sources/practitioner_credibility_criteria.md` | `tracking/eval_log.yaml.md`; `tracking/review_log.md` | `.agent/workflows/eval_iteration_workflow.md` |
| Lessons | `rules/evaluation_gates.md` | `prompts/critic.md` | `sources/source_selection_matrix.md` | `tracking/lesson_log.md`; `tracking/failure_patterns.md` | `.agent/workflows/eval_iteration_workflow.md` |

## Workflow artifact schemas

- Intake: `schemas/task_intel.md`
- Sourcing: `schemas/source_record.md`, `schemas/source_bundle.md`
- Synthesis: `schemas/claim_inventory.md`, `schemas/response_plan.md`
- Verification: `schemas/eval_record.md`, `schemas/approval_manifest.md`, `schemas/source_conflict_record.md`
- Revision control: `schemas/delta_record.md`
- Lessons: `schemas/lesson_record.md`
