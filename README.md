# agentic-workflow-checks-context

This repository holds the reusable context files injected into `agentic-run` during PR reviews.

## Files

- `docs/governance-rules.md` — human-readable governance guidance for Terraform reviews
- `docs/review.md` — concise reviewer rubric used by the workflow

## Intended use

A consumer workflow should check out this repository alongside the target repo and pass these files into `agentic-run` via `extra_context_paths`.
