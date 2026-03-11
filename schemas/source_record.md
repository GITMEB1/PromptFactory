# Schema — source_record

Canonical per-source metadata record used by routing, retrieval, and credibility checks.

## Template
```yaml
source_record:
  source_id: "S-<class>-<nn>"
  class: official|practitioner|private_context|retrieval|model_prior
  title: ""
  source_type: official|retrieval|practitioner|private_context|model_prior
  reference: ""
  locator: ""
  publisher_or_owner: ""
  version_or_date: ""
  retrieved_at: "<ISO-8601|n/a>"
  retrieval_method: "<search|api|manual|n/a>"
  credibility:
    status: pass|review|fail
    rationale: ""
  freshness:
    level: current|aging|stale
    checked_at: "<ISO-8601>"
  usage_constraints: []
```

## Filled example
```yaml
source_record:
  source_id: "S-official-01"
  class: official
  title: "Prompt Factory operating model"
  source_type: official
  reference: "operating_model.md"
  locator: "operating_model.md"
  publisher_or_owner: "Prompt Factory maintainers"
  version_or_date: "2026-03-11"
  retrieved_at: "n/a"
  credibility:
    status: pass
    rationale: "repository canonical workflow document"
  freshness:
    level: current
    checked_at: "2026-03-11T09:20:00Z"
  usage_constraints:
    - "Do not paraphrase lifecycle stage names inconsistently"
```
