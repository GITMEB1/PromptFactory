# Quickstart

## 1) Start at the canonical path

Read in order:
1. [`README.md`](./README.md)
2. [`CANONICAL_EXECUTION_PATH.md`](./CANONICAL_EXECUTION_PATH.md)
3. [`operating_model.md`](./operating_model.md) (concept/policy reference)
4. [`task.md`](./task.md)

## 2) Set up your run

1. Create a task ID (`T-YYYYMMDD-<slug>`).
2. Classify risk (`low|medium|high`) and freshness (`stable|moderate|high`).
3. Select mode using canonical criteria:
   - [`operating_model.md#minimum-evidence-requirements-by-task-risk`](./operating_model.md#minimum-evidence-requirements-by-task-risk)
   - [`operating_model.md#escalation-conditions`](./operating_model.md#escalation-conditions)
4. Define success criteria before sourcing.

## 3) Execute directly via the canonical spine

Follow [`CANONICAL_EXECUTION_PATH.md`](./CANONICAL_EXECUTION_PATH.md) step-by-step:

1. Task Intake
2. Freshness Check
3. Source Routing
4. Retrieval / Reading
5. Credibility Grading
6. Claim Control (Claim Inventory)
7. Response Plan
8. Composition
9. Evaluation (Lint / Eval)
10. Lessons

Use only the rule files, prompt modules, and schema outputs mapped in that file.

## 4) Log outcomes

Record task/run/conflict outcomes in `tracking/`.

## 5) First run examples

### Full exemplar walkthroughs

- [Good exemplar](./examples/good/example.md)
- [Bad exemplar](./examples/bad/example.md)
- [Edge-case exemplar](./examples/edge_cases/example.md)

### Lightweight example (low-stakes, low-freshness)

Use for internal drafts, low-impact summaries, and stable topics. See [`operating_model.md#minimum-evidence-requirements-by-task-risk`](./operating_model.md#minimum-evidence-requirements-by-task-risk) for the governing evidence bar.

#### Example intake (`schemas/task_intel.md`)

```yaml
task_intel:
  task_id: "T-20260311-lightweight-demo"
  title: "Summarize stable repository conventions"
  user_request_verbatim: "Summarize the coding conventions in this repo."
  objective: "Provide a concise, correct summary for internal onboarding."
  audience: "Internal contributors"
  deliverable_type: "answer"
  risk_level: low
  freshness_requirement: stable
  workflow_mode: lightweight
```

#### Example source bundle (`schemas/source_bundle.md`)

```yaml
source_bundle:
  bundle_id: "B-20260311-lightweight-demo"
  task_id: "T-20260311-lightweight-demo"
  source_ids: ["S-private-readme", "S-private-quickstart"]
  class_coverage:
    required: ["private_context"]
    satisfied: ["private_context"]
```

#### Lightweight completion checklist

- Build `claim_inventory` and `response_plan`.
- Run evaluator/lint prompts.
- Deliver with citations and explicit caveats.
- Append task/run entries to `tracking/tasks.yaml.md` and `tracking/runs.yaml.md`.

### Deep example (high-stakes, high-freshness)

Use for externally visible decisions, compliance/safety/legal/financial outputs, or rapidly changing facts. See [`operating_model.md#escalation-conditions`](./operating_model.md#escalation-conditions) and [`operating_model.md#minimum-evidence-requirements-by-task-risk`](./operating_model.md#minimum-evidence-requirements-by-task-risk).

#### Example intake (`schemas/task_intel.md`)

```yaml
task_intel:
  task_id: "T-20260311-deep-demo"
  title: "Assess current feature availability for external guidance"
  user_request_verbatim: "Can we publish that Feature X is production-ready this week?"
  objective: "Provide defensible publish/no-publish guidance based on current evidence."
  audience: "Product + compliance reviewers"
  deliverable_type: "analysis memo"
  risk_level: high
  freshness_requirement: high
  workflow_mode: deep
```

#### Example conflict record (`schemas/source_conflict_record.md`)

```yaml
source_conflict_record:
  conflict_id: "X-007"
  task_id: "T-20260311-deep-demo"
  claim_ids: ["C-004"]
  severity: high
  resolution_status: split_outcome
  rationale: "Official source determines availability; practitioner source adds reliability caveat."
  residual_uncertainty: "region-B performance variability"
```

#### Deep completion checklist

- Create `source_record` entries and a complete `source_bundle`.
- Map decision-critical claims to evidence in `claim_inventory`.
- Record unresolved disagreements with `source_conflict_record`.
- Require evaluation plus `approval_manifest` for high-risk release.
- Append run/conflict entries to `tracking/runs.yaml.md` and `tracking/source_conflicts.yaml.md`.
