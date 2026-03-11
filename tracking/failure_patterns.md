# Failure Patterns (Appendix)

Recurring anti-pattern checks are now maintained in `prompts/evaluator.md` so they are enforced at release-gate time.

Keep this file only for temporary patterns that are not yet stable enough to promote into evaluator guidance.

## Temporary Pattern Template

### FP-XXX — Pattern Name
- **Signal:** Observable symptom in draft/output.
- **Likely Root Cause:** Why it happens.
- **Detection Point:** Intake / Routing / Claims / Output / Eval.
- **Guardrail:** Rule or module to apply.
- **Recovery Playbook:** Steps to remediate in current run.
- **Promotion Trigger:** Number of recurrences before moving to `prompts/evaluator.md`.
