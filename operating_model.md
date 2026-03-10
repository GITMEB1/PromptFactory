# Operating Model

## Purpose

Prompt Factory v2 treats prompting as a **workflow and knowledge-governance problem**, not just a wording problem.

## Canonical execution chain

**Task Intake → Freshness Check → Source Routing → Retrieval / Reading → Credibility Grading → Claim Inventory → Response Plan → Composition → Lint / Eval → Lessons**

## Source precedence

- For unstable facts: **Official + Live Retrieval** outrank everything else.
- For user/project-local truth: **Private primary context** may outrank outside inference.
- For workflow/process advice: **Practitioner sources** may outperform official docs.
- For current uncertainty: do not rely on model memory alone.
- If sources conflict: show the conflict instead of smoothing it over.
