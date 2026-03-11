# Policy Lint Specification

```yaml
checks:
  unsupported_claims:
    severity: fail
    rule_refs: [composition_lock, provenance_policy, source_routing]
    trigger: "Material factual claim lacks source linkage or claim inventory mapping."
    remediation:
      - "Add source citation and provenance metadata."
      - "If no evidence exists, remove claim or mark as speculative."

  stale_high_risk_claims:
    severity: fail
    rule_refs: [freshness_policy, source_routing]
    trigger: "High-risk or volatile claim lacks recent date-anchored verification."
    remediation:
      - "Re-check with current authoritative sources."
      - "Attach date qualifier and lower confidence if recency cannot be confirmed."

  ignored_source_conflict:
    severity: fail
    rule_refs: [conflict_resolution, uncertainty_policy]
    trigger: "Relevant sources disagree but output presents single view without conflict disclosure."
    remediation:
      - "Add conflict note with cause analysis (timeframe, definition, method, scope)."
      - "Recalibrate confidence and recommendation conditions."

  missing_uncertainty_label:
    severity: warn
    rule_refs: [uncertainty_policy]
    trigger: "Inference or estimate presented without confidence/caveat language."
    remediation:
      - "Add calibrated confidence label and key assumptions."
      - "Provide verification steps for decision-critical uncertainty."

  missing_provenance_fields:
    severity: fail
    rule_refs: [provenance_policy]
    trigger: "Citation missing source identity, date, or locator for material claims."
    remediation:
      - "Populate provenance fields in notes and final citations."
      - "Replace unverifiable references with traceable sources."

  disproportional_workflow:
    severity: warn
    rule_refs: [proportionality_policy, eval_policy]
    trigger: "Depth/overhead materially mismatched to user stakes or constraints."
    remediation:
      - "Trim non-essential analysis for low-stakes tasks."
      - "Increase evidence rigor for high-stakes recommendations."

  note_hygiene_violations:
    severity: warn
    rule_refs: [note_hygiene_policy]
    trigger: "Notes mix excerpts/inference, lack staleness markers, or contain unresolved duplicates."
    remediation:
      - "Relabel note sections and deduplicate claim entries."
      - "Add staleness and unresolved-question markers."

  practitioner_overgeneralization:
    severity: warn
    rule_refs: [practitioner_source_policy, credibility_policy]
    trigger: "Anecdotal practitioner evidence presented as universally applicable."
    remediation:
      - "Add context boundaries (environment, scale, version)."
      - "Corroborate with authoritative or independent sources."

  revision_integrity_regression:
    severity: fail
    rule_refs: [revision_policy, composition_lock]
    trigger: "Revision introduces unsupported claims or drops critical caveats/citations."
    remediation:
      - "Run post-revision claim-to-source reconciliation."
      - "Restore missing caveats/citations and re-run lint."

  generic_language:
    severity: warn
    rule_refs: [eval_policy]
    trigger: "Output uses vague phrasing that obscures concrete guidance."
    remediation:
      - "Replace generic text with specific, evidence-grounded statements."

  redundant_context:
    severity: warn
    rule_refs: [proportionality_policy, eval_policy]
    trigger: "Repeated background/context reduces clarity and actionability."
    remediation:
      - "Collapse repeated context into one concise section."

  low_vitality_prose:
    severity: warn
    rule_refs: [eval_policy]
    trigger: "Monotone or passive-heavy prose reduces readability."
    remediation:
      - "Tighten sentence structure and prefer direct active language."

  tone_drift:
    severity: warn
    rule_refs: [eval_policy]
    trigger: "Tone diverges from user intent or domain expectations."
    remediation:
      - "Align tone to audience and requested format."

  workflow_overhead:
    severity: warn
    rule_refs: [proportionality_policy]
    trigger: "Process steps exceed task needs without quality benefit."
    remediation:
      - "Remove low-value checks and focus on risk-relevant controls."
```
