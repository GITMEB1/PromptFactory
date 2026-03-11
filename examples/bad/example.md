# Bad Example — Compliance Recommendation from Stale Community Threads

## 1) Intake
- **User request:** "Can we treat new audit logging controls as optional until next year?"
- **Task profile:** High-risk compliance interpretation.

## 2) Routing (what went wrong)
- **Mode selected:** Lightweight (incorrect for risk level).
- **Source classes used:**
  - **Practitioner only:** Community forum and two blog posts.
  - **Official:** Not consulted.
  - **Private context:** Not consulted.
  - **Model prior:** Filled gaps in policy language.
- **Freshness handling failure:**
  - One blog was 14 months old.
  - No date check or staleness caveat was provided.

## 3) Claims (problematic)
1. **Claim:** "Audit logging controls remain optional until next year."
   - Unsupported by official policy docs.
2. **Claim:** "Most companies are delaying adoption anyway."
   - Anecdotal practitioner claim generalized into policy advice.

## 4) Output (abridged)
> You can likely defer implementation until next year, since enforcement appears soft and peers are waiting.

- **Source-class distinction failure:** Community anecdotes were treated as normative authority.
- **Freshness failure:** Outdated guidance presented as current.

## 5) Eval
- **Grounding:** 1/5
- **Source quality mix:** 1/5
- **Freshness handling:** 1/5
- **Uncertainty calibration:** 1/5
- **Overall:** Revise (critical)

## Corrective Path
1. Re-route through official compliance bulletin and current regulator guidance.
2. Cross-check against internal audit commitments (private context).
3. Add explicit freshness statement and conservative uncertainty language.
4. Log FP-001 and FP-002 in `tracking/failure_patterns.md`.
