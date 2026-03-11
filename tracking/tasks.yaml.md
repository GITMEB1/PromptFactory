# Tracking Template — Tasks

Use this template to track incoming work before execution.

**Schema alignment:** each entry nests `task_intel` and uses the exact key names from `schemas/task_intel.md`.

```yaml
tasks:
  - task_intel:
      task_id: "T-YYYYMMDD-001"
      title: "Short task title"
      user_request_verbatim: "Original user request text"
      objective: "One-sentence target outcome"
      audience: "team-or-user"
      deliverable_type: "answer|analysis memo|documentation patch"
      risk_level: low|medium|high
      freshness_requirement: stable|moderate|high
      workflow_mode: lightweight|deep
      scope:
        in_scope:
          - "In-scope item"
        out_of_scope:
          - "Out-of-scope item"
      source_constraints:
        required_classes:
          - "official"
        prohibited_classes:
          - "model_prior_only"
        citation_requirements: "Formatting requirements"
      success_definition:
        - "All deliverables updated"
        - "Eval score >= 4 on grounding"
      assumptions:
        - assumption: "Primary uncertainty"
          status: confirmed|unconfirmed
      missing_information_requests: []
```
