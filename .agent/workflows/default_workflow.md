# Default Workflow (Orchestrator)

## When to use
Use as the primary orchestrator for most tasks. This workflow now contains mode switches for implementation, research, writing, analysis, and review so execution stays in one control plane.

## Inputs
- Task request and acceptance criteria
- Relevant repository policies and docs
- Current repository state
- Known constraints (time, tooling, risk tolerance)

## Orchestration sequence
1. Triage scope, risk, deliverables, and deadline.
2. Choose the active mode using the selector table.
3. Execute that mode's gated sequence.
4. If task state changes, switch mode and record why.
5. Validate outcomes and publish handoff artifacts.

### Mode selector
| Mode | Trigger signal | Gate to enter | Gate to exit |
|---|---|---|---|
| `implementation` | Concrete change can be made now | Scope and files to edit are identified | Changes implemented and checks executed |
| `research` | Missing context/evidence before editing | Research questions and quality bar are explicit | Findings mapped to decisions with confidence notes |
| `writing` | Deliverable quality depends on narrative structure/tone | Audience, purpose, and constraints are explicit | Draft passes clarity/completeness pass |
| `analysis` | Need option comparison, decomposition, or root cause | Criteria and assumptions are defined | Recommendation and trade-off rationale are documented |
| `review` | Need QA/verification/critique of existing artifact | Review rubric/acceptance criteria are explicit | Findings severity-ranked and decision recorded |
| `source-conflict` | Sources disagree materially | Conflicting claims are isolated and cited | Resolution (or preserved ambiguity) is documented |
| `eval-iteration` | Requires measurable iterative tuning | Metrics, thresholds, and stop conditions are set | Iteration delta logged and keep/revert decision made |

## Mode playbooks

### Implementation mode
1. Plan edits in small, reviewable increments.
2. Implement changes.
3. Run targeted checks.
4. Record results and residual risk.

### Research mode (inline)
1. Define research objectives and evidence quality bar.
2. Gather sources by authority and relevance.
3. Extract findings mapped to task decisions.
4. Record unresolved gaps and confidence per finding.

### Writing mode (inline)
1. Define audience, purpose, and success criteria.
2. Build outline with section intent.
3. Draft for factual correctness and flow.
4. Edit for concision, coherence, and terminology consistency.
5. Run final references/format/completeness pass.

### Analysis mode (inline)
1. Frame decision/problem boundaries.
2. Decompose into options or hypotheses.
3. Evaluate against criteria using available evidence.
4. Synthesize trade-offs and recommendation.
5. Document assumptions and sensitivity to new evidence.

### Review mode (inline)
1. Confirm scope and quality bar.
2. Inspect artifacts systematically against criteria.
3. Record findings by severity.
4. Verify fixes (or provide actionable remediation).
5. Record go/no-go decision and residual risk.

### Specialized mode delegation
- For materially distinct source acquisition procedures, delegate to `research_workflow.md`.
- For source disagreement resolution, delegate to `source_conflict_workflow.md`.
- For metric-driven iterative tuning, delegate to `eval_iteration_workflow.md`.

## Outputs
- Completed changes aligned to task scope
- Validation results with pass/fail notes
- Decision/rationale artifacts produced by active mode(s)
- Explicit next-step recommendation

## Failure conditions
- Requirements are ambiguous and cannot be bounded.
- Required files, tools, or evidence are unavailable.
- Validation cannot be executed or interpreted confidently.

## Handoff contract
Every handoff from this orchestrator must include:
1. **Active mode history:** mode order and reason for each switch.
2. **Completion status:** done/in-progress/not-started per deliverable.
3. **Evidence pack:** checks run, key findings, and confidence level.
4. **Open risks:** blockers, assumptions, and owner-needed decisions.
5. **Next action:** single concrete next step with expected output.
