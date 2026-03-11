# First Real Run

This guide helps you execute your first end-to-end Prompt Factory run with auditable artifacts.

## Preconditions

- You have read: `README.md`, `operating_model.md`, and `QUICKSTART.md`.
- You can edit files in `schemas/`-aligned formats and append records in `tracking/` templates.

## Run setup checklist

1. Create a task ID (`T-YYYYMMDD-<slug>`).
2. Classify risk (`low|medium|high`) and freshness (`stable|moderate|high`).
3. Select mode:
   - `lightweight` for low-stakes + low-freshness tasks.
   - `deep` for high-stakes and/or high-freshness tasks.
4. Define success criteria before sourcing.

## Walkthrough A — Lightweight path (low-stakes, low-freshness)

Use this path for internal drafts, low-impact summaries, and stable topics.

### Step 1: Intake artifact (`schemas/task_intel.md`)

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
  scope:
    in_scope: ["existing repository docs"]
    out_of_scope: ["new policy design"]
  source_constraints:
    required_classes: ["private_context"]
    prohibited_classes: ["model_prior_only"]
    citation_requirements: "file-line citations"
  success_definition:
    - "summary matches current docs"
    - "all material claims cite repo files"
  assumptions:
    - assumption: "repository docs are current"
      status: confirmed
  missing_information_requests: []
```

### Step 2: Source package (`schemas/source_bundle.md`)

```yaml
source_bundle:
  bundle_id: "B-20260311-lightweight-demo"
  task_id: "T-20260311-lightweight-demo"
  owner: "operator"
  created_at: "2026-03-11T10:00:00Z"
  source_ids: ["S-private-readme", "S-private-quickstart"]
  class_coverage:
    required: ["private_context"]
    satisfied: ["private_context"]
  claim_links:
    - claim_id: "C-001"
      source_ids: ["S-private-readme"]
  conflicts: []
  notes: "No external retrieval required for stable internal summary."
```

### Step 3: Plan + evaluate

- Build `claim_inventory` and `response_plan` artifacts.
- Run evaluator/lint prompts.
- If pass, deliver with explicit caveats.

### Step 4: Track run (`tracking/tasks.yaml.md`, `tracking/runs.yaml.md`)

- Add a task record with `routing_hint.mode: lightweight`.
- Add a run record with `mode: lightweight`, module path, outcome, and artifacts.

---

## Walkthrough B — Deep path (high-stakes, high-freshness + source conflict handling)

Use this path for externally visible decisions, compliance, safety, legal/financial content, or rapidly changing facts.

### Step 1: Intake artifact (`schemas/task_intel.md`)

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
  scope:
    in_scope: ["current feature status", "release criteria"]
    out_of_scope: ["roadmap speculation"]
  source_constraints:
    required_classes: ["official", "retrieval", "private_context"]
    prohibited_classes: ["model_prior_only"]
    citation_requirements: "claim-level citations + conflict disclosure"
  success_definition:
    - "all decision-critical claims supported by authoritative sources"
    - "source conflicts explicitly resolved or escalated"
  assumptions:
    - assumption: "official status can change daily"
      status: confirmed
  missing_information_requests: []
```

### Step 2: Build source bundle and detect conflict

- Create `source_record` entries for each source.
- Compile a `source_bundle` with claim-to-source links.
- If sources disagree, create a `source_conflict_record`.

```yaml
source_conflict_record:
  conflict_id: "X-007"
  task_id: "T-20260311-deep-demo"
  claim_ids: ["C-004"]
  competing_sources:
    - source_id: "S-official-1"
      position_summary: "Feature X is GA in regions A/B only"
    - source_id: "S-practitioner-2"
      position_summary: "Feature X appears unstable in region B"
  severity: high
  resolution_status: split_outcome
  rationale: "Official source is authoritative for availability, practitioner source informs operational caveat."
  winning_or_split_outcome: "Publish conditional availability with reliability caveat and scope limits."
  residual_uncertainty: "region-B performance variability"
```

### Step 3: Verification and approvals

- Run eval checks and record in `schemas/eval_record.md` format.
- For high-risk output, produce `approval_manifest` and require sign-off.

### Step 4: Track conflict and run

- Append conflict to `tracking/source_conflicts.yaml.md`.
- Append run metadata to `tracking/runs.yaml.md` including freshness checks and disclosures.

## Common failure and recovery

1. **Failure: Wrong mode selected (lightweight used for high-risk/high-freshness).**
   - Recovery: Reclassify task in `task_intel`, switch to `deep`, and restart from sourcing.
2. **Failure: Claims lack explicit source links.**
   - Recovery: Rebuild `claim_inventory` with source IDs per claim before composition.
3. **Failure: Conflict detected but not documented.**
   - Recovery: Create `source_conflict_record` and add a tracking entry in `tracking/source_conflicts.yaml.md`.
4. **Failure: Delivered answer hides uncertainty.**
   - Recovery: Update response plan to force caveats/disclosures for unresolved evidence.
