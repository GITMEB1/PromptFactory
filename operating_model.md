# Operating Model

## Purpose

Prompt Factory v2 treats prompting as a **workflow and knowledge-governance problem**, not just a wording problem.

## Lifecycle stages

1. **Intake**
   - Capture task requirements in `task.md`
   - Classify risk, freshness, and deliverable type
2. **Scoping**
   - Select lightweight or deep mode
   - Define acceptable uncertainty and response boundaries
3. **Sourcing**
   - Route required claims to source classes
   - Gather evidence from official, practitioner, private context, retrieval, or bounded prior
4. **Synthesis**
   - Build claim inventory and response plan
   - Track confidence and unresolved gaps
5. **Verification**
   - Run lint/eval checks and contradiction checks
   - Ensure minimum evidence requirements are met
6. **Delivery**
   - Produce final response with caveats and references
7. **Post-run learning**
   - Log outcome, conflicts, and improvements in `tracking/*`

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
- For current uncertainty: do not rely on model memory alone.
- If sources conflict: show the conflict instead of smoothing it over.

## Canonical execution chain

**Task Intake → Freshness Check → Source Routing → Retrieval / Reading → Credibility Grading → Claim Inventory → Response Plan → Composition → Lint / Eval → Lessons**

## Workflow artifact schemas

- Intake: `schemas/task_intel.md`
- Sourcing: `schemas/source_record.md`, `schemas/source_bundle.md`
- Synthesis: `schemas/claim_inventory.md`, `schemas/response_plan.md`
- Verification: `schemas/eval_record.md`, `schemas/approval_manifest.md`, `schemas/source_conflict_record.md`
- Revision control: `schemas/delta_record.md`
- Post-run learning: `schemas/lesson_record.md`
