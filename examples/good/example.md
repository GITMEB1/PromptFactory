# Good Example — Vendor API Deprecation Guidance

## 1) Intake
- **User request:** "Should we migrate from API v1 to v2 this quarter, and what risks should leadership know?"
- **Task profile:** Decision support with moderate risk and external dependencies.
- **Success bar:** Recommendation must be grounded in source evidence, explicitly date-aware, and include uncertainty notes.

## 2) Routing
- **Mode selected:** Deep mode.
- **Source classes chosen:**
  - **Official:** "Vendor API Lifecycle Policy — v1 Sunset Bulletin" (`official`, reference: `https://vendor.example.com/bulletins/v1-sunset`, updated 2026-04-22).
  - **Retrieval:** "Vendor Status Changelog — API v2 Migration Notes" (`retrieval`, reference: `https://vendor.example.com/changelog/api-v2-migration`, retrieved 2026-04-24T10:12:00Z via web search).
  - **Practitioner:** "Auth Middleware Migration Postmortem (Team A)" (`practitioner`, reference: `https://engineering.example.net/postmortems/auth-mw-v2`).
  - **Private context:** "Gateway Dependency Inventory Q2" (`private_context`, reference: `internal/wiki/gateway-deps-q2`).
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
- **Evidence integrity:** pass (required classes `official` + `retrieval` explicitly satisfied; provenance quality `exact`; artifact accounting consistent as consolidated report)
- **Overall:** Ship
- **Lesson captured:** Keep practitioner estimates separate from official commitments.
