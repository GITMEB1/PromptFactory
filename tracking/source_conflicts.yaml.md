# Tracking Template — Source Conflicts

Use this template when sources disagree materially.

**Schema alignment:** each entry nests `source_conflict_record` and uses exact key names from `schemas/source_conflict_record.md`.

```yaml
source_conflicts:
  - source_conflict_record:
      conflict_id: "X-001"
      task_id: "T-YYYYMMDD-001"
      claim_ids:
        - "C-004"
      competing_sources:
        - source_id: "src-official-1"
          position_summary: "Feature X is generally available in all regions"
        - source_id: "src-practitioner-2"
          position_summary: "Feature X has reliability limits in region B"
      severity: low|medium|high
      resolution_status: resolved|split_outcome|unresolved
      rationale: "Prefer newer official source and preserve practitioner caveat"
      winning_or_split_outcome: "GA overall, with explicit region-B caveat"
      residual_uncertainty: "region-B performance variability"
```
