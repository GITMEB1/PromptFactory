# Exemplar Index

Index of complete scenario walkthroughs that demonstrate intake → routing → claims → output → eval.

## Good Exemplars
- [`examples/good/example.md`](../examples/good/example.md)
  - Highlights balanced source classes and explicit freshness caveats.
  - Key modules: `prompts/task_intake.md`, `prompts/source_router.md`, `prompts/claim_builder.md`, `prompts/evaluator.md`.
  - Key rules: `rules/source_routing.md`, `rules/freshness_policy.md`, `rules/uncertainty_policy.md`.

## Bad Exemplars
- [`examples/bad/example.md`](../examples/bad/example.md)
  - Demonstrates overreliance on one source class and freshness violations.
  - Recovery references: `tracking/failure_patterns.md` (FP-001, FP-002).
  - Key rules violated: `rules/source_routing.md`, `rules/freshness_policy.md`, `rules/provenance_policy.md`.

## Edge-Case Exemplars
- [`examples/edge_cases/example.md`](../examples/edge_cases/example.md)
  - Covers conflicting, mixed-freshness sources and conditional recommendations.
  - Key modules: `prompts/source_conflict_resolver.md`, `prompts/freshness_checker.md`, `prompts/final_response_builder.md`.
  - Key rules: `rules/conflict_resolution.md`, `rules/freshness_policy.md`, `rules/proportionality_policy.md`.

## How to Use This Index
1. Pick an exemplar matching your risk profile.
2. Reuse its stage structure for run notes.
3. Copy lessons into `tracking/lesson_log.md` and anti-patterns into `tracking/failure_patterns.md`.
