# Schema — source_bundle

Evidence package that groups all selected sources for a run.

## Template
```yaml
source_bundle:
  bundle_id: "B-<YYYYMMDD>-<task_slug>"
  task_id: ""
  owner: ""
  created_at: "<ISO-8601>"
  source_ids: []
  class_coverage:
    required: []
    satisfied: []
    missing: []
  claim_links:
    - claim_id: ""
      source_ids: []
      support_type: direct_evidence|inferential_synthesis|contextual_constraint
  provenance_quality: exact|mixed|vague
  artifacts_declared:
    format: consolidated|separate
    files: []
  artifacts_produced:
    format: consolidated|separate
    files: []
  conflicts: []
  notes: ""
```

## Filled example
```yaml
source_bundle:
  bundle_id: "B-20260311-schemas"
  task_id: "T-20260311-promptfactory-schemas"
  owner: "codex"
  created_at: "2026-03-11T09:28:00Z"
  source_ids: ["S-private-01", "S-private-02"]
  class_coverage:
    required: ["private_context"]
    satisfied: ["private_context"]
    missing: []
  claim_links:
    - claim_id: "C-001"
      source_ids: ["S-private-01"]
      support_type: contextual_constraint
  provenance_quality: exact
  artifacts_declared:
    format: consolidated
    files: ["artifacts/run_report.md"]
  artifacts_produced:
    format: consolidated
    files: ["artifacts/run_report.md"]
  conflicts: []
  notes: "Repository-local docs were sufficient; no external retrieval used."
```
