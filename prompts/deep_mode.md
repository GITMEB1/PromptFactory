# Prompt Module — Deep Mode

## Trigger
- Use for high-risk, high-freshness, high-visibility, or contested tasks.
- Trigger from intake recommendation, evaluator failure, or explicit user requirement.

## Inputs
- **Required**
  - `task_profile` indicating elevated assurance needs.
  - `source_plan` with authoritative coverage.
  - Full module artifacts (retrieval, claims, conflicts, uncertainty).
  - Canonical policy files:
    - `rules/source_discipline.md`
    - `rules/claim_safety.md`
    - `rules/conflict_and_uncertainty.md`
    - `rules/evaluation_gates.md`
    - `rules/proportionality.md`
- **Optional**
  - External review rubric or stakeholder acceptance criteria.
  - Prior failed drafts for targeted remediation.

## Procedure
1. Consult rule: `rules/proportionality.md`.
2. Execute step: confirm deep workflow is required for stated stakes.
3. Consult rule: `rules/source_discipline.md`.
4. Execute step: run source routing with class redundancy and freshness-aware retrieval.
5. Consult rule: `rules/claim_safety.md`.
6. Execute step: perform claim atomization and claim-to-source trace binding.
7. Consult rule: `rules/conflict_and_uncertainty.md`.
8. Execute step: resolve conflicts and document residual uncertainty.
9. Consult rule: `rules/evaluation_gates.md`.
10. Execute step: run evaluator/critic loops until blocking issues are resolved or explicitly deferred.

## Outputs
- `deep_execution_record` spanning all module artifacts.
- `high_assurance_claim_inventory` with full traceability.
- `review_ready_response` plus unresolved-risk disclosures.

## Failure patterns
- **Symptom:** Deep workflow produces volume without decision clarity.
  - Consult rule: `rules/proportionality.md`.
  - Execute step: add stage-level synthesis checkpoints.
- **Symptom:** Revision loops do not converge.
  - Consult rule: `rules/evaluation_gates.md`.
  - Execute step: enforce explicit closure criteria from blocking issues.
- **Symptom:** High assurance claimed with weak provenance.
  - Consult rule: `rules/claim_safety.md`.
  - Execute step: run trace audit and block finalization until fixed.
