# Source Bundle Template

Use this template to assemble a mixed-source evidence pack for a run.

## Bundle Header
```yaml
bundle_id: B-YYYYMMDD-<task_slug>
task_summary: "<one-line task>"
risk_level: low|medium|high
freshness_need: low|medium|high
owner: "<agent/user/team>"
created_at: "<ISO-8601>"
```

## Required Sections

### 1) Source Inventory
```yaml
sources:
  - source_id: S-official-01
    class: official
    title: "<doc title>"
    locator: "<url/doc-id/path>"
    version_or_date: "<value>"
    retrieved_at: "<ISO-8601 or n/a>"
    credibility_status: pass

  - source_id: S-private-01
    class: private_context
    title: "<internal runbook>"
    locator: "<path/ref>"
    version_or_date: "<value>"
    retrieved_at: "n/a"
    credibility_status: pass
```

### 2) Claim Map
```yaml
claims:
  - claim_id: C-001
    text: "<claim text>"
    supports_decision: true
    stale_risk: high
    source_ids: [S-official-01, S-retrieval-02]
    confidence: medium
```

### 3) Coverage Check
- Required source classes present per `sources/source_selection_matrix.md`.
- Freshness thresholds satisfied per `sources/freshness_risk_matrix.md`.
- Practitioner sources pass `sources/practitioner_credibility_criteria.md`.

### 4) Conflict Log
```yaml
conflicts:
  - conflict_id: X-001
    claim_ids: [C-004, C-007]
    status: unresolved
    user_visible_note: "Official and practitioner guidance differ for v3 defaults."
```

### 5) Output Constraints
```yaml
constraints:
  - "Do not expose private locator details in final response."
  - "Tag unresolved high-risk claims as verification required."
```

## Assembly Checklist
- Select required source classes first (risk + freshness driven).
- Add only sources directly used by at least one claim.
- Ensure each consequential claim has explicit provenance.
- Annotate unresolved conflicts before final synthesis.
