# Edge Case Example — Conflicting Release Status Across Source Classes

## 1) Intake
- **User request:** "Is feature flagless SSO rollout complete globally, and should we remove fallback auth?"
- **Task profile:** Medium-high risk; operational outage potential.

## 2) Routing
- **Mode selected:** Deep mode with explicit conflict resolution.
- **Source classes chosen:**
  - **Official:** Product status page + release changelog.
  - **Practitioner:** Recent issue threads and implementer notes from partner community.
  - **Private context:** Internal incident dashboard and regional traffic logs.
  - **Model prior:** Only for structuring conditional recommendation language.
- **Freshness handling:**
  - Official status page updated 2 days ago.
  - Practitioner thread updated today but includes unverified reports.
  - Internal logs updated hourly and treated as most current for local impact.

## 3) Claims
1. **Claim:** Official docs indicate global rollout complete.
2. **Counter-claim:** Practitioner reports show APAC tenants still seeing fallback prompts.
3. **Internal evidence:** 6% APAC auth traffic hits fallback path in last 24h.
4. **Resolution:** Treat rollout as "nominally complete" but operationally incomplete for APAC; defer fallback removal globally.

## 4) Output (abridged)
> Do not remove fallback auth globally yet. Keep fallback enabled in APAC and run a 72-hour stability watch. Official release status suggests completion, but fresher partner reports and internal telemetry show residual fallback usage. Re-evaluate after APAC fallback traffic is <1% for three consecutive days.

- **Source-class distinction in output:**
  - Official source defines intended state.
  - Practitioner + private context define observed state and risk.
- **Freshness treatment in output:**
  - Prioritizes hourly internal telemetry over older but authoritative release declaration for immediate operational decision.

## 5) Eval
- **Grounding:** 4/5
- **Source quality mix:** 5/5
- **Freshness handling:** 5/5
- **Uncertainty calibration:** 5/5
- **Overall:** Ship with monitoring condition
- **Follow-up:** Record conflict in `tracking/source_conflicts.yaml.md` and lesson in `tracking/lesson_log.md`.
