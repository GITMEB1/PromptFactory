# Default Workflow

## When to use
Use for general implementation tasks that do not clearly require a specialized workflow.

## Inputs
- Task request and acceptance criteria
- Relevant repository policies and docs
- Current repository state

## Sequence
1. Triage request scope, risk, and deliverables.
2. Use the workflow selector table to choose specialized workflow(s) when needed.
3. Plan work, identify files, and define validation checks.
4. Implement changes in small, reviewable increments.
5. Run checks, summarize outcomes, and prepare handoff artifacts.

### Workflow selector table
| Task characteristic | Primary workflow | Trigger signal |
|---|---|---|
| Unknown domain, missing background, or evidence gaps | `research_workflow.md` | Need to collect context before editing |
| Drafting or refining long-form narrative deliverables | `writing_workflow.md` | Output quality depends on structure/tone clarity |
| Root-cause analysis, comparisons, or decision decomposition | `analysis_workflow.md` | Requires explicit reasoning or option evaluation |
| QA pass, verification, regression checks, or critique | `review_workflow.md` | Goal is to validate/assess existing work |
| Conflicting claims or contradictory sources | `source_conflict_workflow.md` | Evidence sources disagree materially |
| Repeated evaluation and prompt/policy tuning loop | `eval_iteration_workflow.md` | Need metric-driven iterative improvement |
| None of the above | `default_workflow.md` | Standard implementation path |

## Outputs
- Completed changes aligned to task scope
- Validation results with pass/fail notes
- Concise summary and explicit next steps

## Failure conditions
- Requirements are ambiguous and cannot be bounded.
- Required files, tools, or evidence are unavailable.
- Validation cannot be executed or interpreted confidently.

## Handoff
Provide current status, what was completed, open issues, and the next concrete action for continuation.
