# Schema — task_intel

Use this schema to normalize intake output from `prompts/task_intake.md`.

## Template
```yaml
task_intel:
  task_id: "T-<YYYYMMDD>-<slug>"
  title: ""
  user_request_verbatim: ""
  objective: ""
  audience: ""
  deliverable_type: ""
  risk_level: low|medium|high
  freshness_requirement: stable|moderate|high
  workflow_mode: lightweight|deep
  scope:
    in_scope: []
    out_of_scope: []
  source_constraints:
    required_classes: []
    prohibited_classes: []
    citation_requirements: ""
  success_definition: []
  assumptions:
    - assumption: ""
      status: confirmed|unconfirmed
  missing_information_requests: []
```

## Filled example
```yaml
task_intel:
  task_id: "T-20260311-promptfactory-schemas"
  title: "Add auditable schemas and references"
  user_request_verbatim: "Create schemas and cross-reference docs."
  objective: "Add reusable schema artifacts for workflow records."
  audience: "Prompt Factory maintainers"
  deliverable_type: "documentation patch"
  risk_level: medium
  freshness_requirement: stable
  workflow_mode: deep
  scope:
    in_scope: ["schema templates", "doc cross-links"]
    out_of_scope: ["policy rewrites", "new runtime tooling"]
  source_constraints:
    required_classes: ["private_context"]
    prohibited_classes: ["model_prior_only"]
    citation_requirements: "file-line citations in final answer"
  success_definition:
    - "all requested schema files exist"
    - "each schema includes one concrete example"
    - "workflow and prompt docs reference relevant schemas"
  assumptions:
    - assumption: "existing docs are the source of truth for stage names"
      status: confirmed
  missing_information_requests: []
```
