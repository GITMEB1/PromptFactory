# Tracking Template — Source Conflicts

Use this template when sources disagree materially.

```yaml
source_conflicts:
  - conflict_id: SC-YYYYMMDD-001
    run_id: R-YYYYMMDD-001
    claim: "Feature X is generally available"
    conflicting_sources:
      - id: src-official-1
        class: official
        citation: "Vendor changelog (2026-01-10)"
        stance: supports
      - id: src-practitioner-2
        class: practitioner
        citation: "Engineer blog (2025-12-01)"
        stance: contradicts
    conflict_type: recency|scope|terminology|factual
    freshness_snapshot:
      newest_source_age_days: 4
      oldest_source_age_days: 44
      policy_window_days: 30
    resolution_strategy:
      applied_rule: rules/conflict_resolution.md
      decision: "Prefer newer official source; keep practitioner as caveat"
    impact_on_output:
      confidence_adjustment: "medium -> medium-high"
      required_disclosure: true
      disclosure_text: "Community reports may reflect pre-GA behavior"
```
