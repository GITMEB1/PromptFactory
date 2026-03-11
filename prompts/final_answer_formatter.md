# Prompt Module — Final Answer Formatter

## When invoked
- Final stage after evaluator/critic revisions are complete.
- Triggered when output must be transformed into delivery-ready format.
- Requires approved draft and formatting constraints.

## Inputs
- **Required**
  - Final approved draft text.
  - Delivery format requirements (markdown style, headings, bullets, citation style).
  - Mandatory disclosure blocks (if any).
- **Optional**
  - Channel-specific length limits.
  - Localization or terminology preferences.

## Procedure
1. Apply required structural template (sections, heading levels, list style).
2. Normalize citation/disclosure formatting to house rules.
3. Enforce brevity or detail targets by audience/channel.
4. Run final consistency sweep for terminology and units.
5. Ensure unresolved uncertainties are disclosed in final text.
6. Emit final answer artifact and lightweight delivery checklist.

## Outputs
- `final_answer` in delivery-ready format.
- `formatting_checklist` with pass/fail items.
- `post_delivery_notes` (optional known limitations).

## Quality checks
- Output matches required structural template exactly.
- Citation and disclosure formatting is consistent.
- Terminology is internally consistent.
- No tracked blocking issue remains unresolved.

## Failure patterns
- **Symptom:** Strong content rejected for formatting mismatch.
  - Cause: Template rules applied late or inconsistently.
  - Fix: Run formatter as dedicated final stage.
- **Symptom:** Citations break after edits.
  - Cause: Final normalization skipped.
  - Fix: Re-run citation formatting pass.
- **Symptom:** Final message hides unresolved risks.
  - Cause: Disclosure blocks dropped in formatting.
  - Fix: Add mandatory disclosure check item.
