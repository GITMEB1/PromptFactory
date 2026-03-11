# Prompt Module — Final Response Builder

## When invoked
- After `claim_builder` output is approved and post-draft `evaluator` checks are complete.
- Triggered to build the delivery-ready response in one controlled module.
- Requires approved claims, user format constraints, and disclosure requirements.

## Inputs
- **Required**
  - Approved `claim_inventory` entries.
  - User deliverable constraints (format, length, tone, required sections).
  - `evaluation_report` + blocking fix status.
- **Optional**
  - `uncertainty_language_pack` from `uncertainty_writer`.
  - `critique_report` from adversarial `critic` pass.

## Procedure

### 1) Structure plan
1. Build a section outline that mirrors explicit user requirements.
2. Map each section to approved claim IDs and evidence density expectations.
3. Place disclosure slots where decisions depend on uncertainty, conflicts, or freshness limits.
4. Confirm all critical user questions are covered by at least one approved claim.

### 2) Draft from approved claims
1. Draft each section using only mapped, approved claims.
2. Keep evidence-backed statements distinct from recommendations.
3. Apply calibrated wording for provisional, contested, or low-confidence claims.
4. Record claim usage by section; remove unsupported filler or speculative additions.

### 3) Final formatting and disclosure checks
1. Apply required delivery format (heading levels, bullet style, citation style).
2. Normalize terminology, units, and naming consistency.
3. Verify unresolved uncertainty/conflict disclosures are present at decision-relevant points.
4. Confirm no evaluator blocking issue remains unresolved.
5. Verify artifact accounting consistency: declared artifact format/files match produced format/files (consolidated vs separate).
6. Emit final answer artifact plus checklist.

## Outputs
- `final_answer` (delivery-ready text).
- `response_blueprint` (section plan + mapped claims).
- `claim_usage_log` (claim IDs used per section).
- `formatting_checklist` (pass/fail items).
- `open_issues` (remaining non-blocking gaps).

## Quality checks
- Every substantive statement maps to an approved claim.
- User-required structure/constraints are fully represented.
- Formatting and citation/disclosure rules are consistent end-to-end.
- Known uncertainty is explicit where it could change user decisions.

## Failure patterns
- **Symptom:** Fluent draft misses a required user section.
  - Cause: Structure plan skipped requirement mapping.
  - Fix: Rebuild section-to-requirement coverage before redrafting.
- **Symptom:** Draft introduces plausible but unsupported facts.
  - Cause: Authoring exceeded approved claim set.
  - Fix: Enforce claim usage log and remove unmapped statements.
- **Symptom:** Final output is polished but hides material uncertainty.
  - Cause: Disclosure slots were not preserved through formatting.
  - Fix: Run mandatory disclosure checkpoint before release.

## Schema references
- `schemas/response_plan.md` — section/claim mapping model.
- `schemas/claim_inventory.md` — approved claims and support status.
- `schemas/eval_record.md` — evaluator gate results and blocking issue status.
