# Model Prior Usage Policy

Model prior is latent knowledge already in-model before the run. It is useful for scaffolding, but never a substitute for required evidence.

## Criteria
- Claim is low-risk, stable, and unlikely to change materially.
- Statement is generic background or widely invariant concept.
- No stronger source class is required by task policy.
- Confidence is explicit and uncertainty can be surfaced.

## Allowed Usage
- Draft initial hypotheses, taxonomies, and candidate approaches.
- Provide non-critical explanatory context when stakes are low.
- Bridge missing details while clearly marking assumptions.
- Accelerate synthesis after official/private/retrieval sources establish critical facts.

## Failure Modes
- **Hallucinated specifics**: fabricated versions, APIs, or policy details.
- **Temporal drift**: outdated facts treated as current.
- **Authority inversion**: prior overrides contradictory official/private evidence.
- **Confidence inflation**: uncertain memory presented as verified fact.

## Guardrail
If a fact may have changed, do not let memory settle it.
