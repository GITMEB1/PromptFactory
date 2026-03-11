# Good Example — Vendor API Deprecation Guidance

## 1) Intake
- **User request:** "Should we migrate from API v1 to v2 this quarter, and what risks should leadership know?"
- **Task profile:** Decision support with moderate risk and external dependencies.
- **Success bar:** Recommendation must be grounded in source evidence, explicitly date-aware, and include uncertainty notes.

## 2) Routing
- **Mode selected:** Deep mode.
- **Source classes chosen:**
  - **Official:** Vendor deprecation notice and release notes (normative dates and support commitments).
  - **Practitioner:** Two engineering postmortems from teams that migrated recently (migration pitfalls).
  - **Private context:** Internal service inventory and dependency map (blast radius).
  - **Model prior:** Used only for drafting migration sequencing language, never as sole evidence.
- **Freshness handling:**
  - Official sources required within 30 days for timelines.
  - Practitioner sources accepted up to 180 days but labeled as contextual.
  - Internal inventory timestamp verified as updated this week.

## 3) Claims
1. **Claim:** API v1 enters security-fix-only mode on 2026-05-01.
   - Source class: Official (high authority, high freshness).
2. **Claim:** Teams with custom auth middleware saw a 2–3 sprint migration overhead.
   - Source class: Practitioner (medium authority, medium freshness).
3. **Claim:** 38% of our endpoints still depend on v1 through shared gateway policy.
   - Source class: Private context (high relevance, high freshness).
4. **Claim confidence adjustment:** Reduced confidence on effort estimate due to heterogeneity across practitioner cases.

## 4) Output (abridged)
> Migrate this quarter in two waves. Wave 1 should cover low-coupling services by end of next sprint; wave 2 should include auth-heavy services with explicit buffer. The deprecation timeline is strongly supported by current vendor docs, while effort estimates are directional and based on recent external team reports. If gateway policy ownership changes, reassess projected effort.

- **Source-class distinction in output:** Normative timelines attributed to official documents; operational risk estimates attributed to practitioner/internal evidence.
- **Freshness disclosure in output:** "Timeline data verified against vendor release notes updated 8 days ago."

## 5) Eval
- **Grounding:** 5/5
- **Source quality mix:** 5/5
- **Freshness handling:** 5/5
- **Uncertainty calibration:** 4/5
- **Overall:** Ship
- **Lesson captured:** Keep practitioner estimates separate from official commitments.
