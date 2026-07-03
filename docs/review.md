---
name: terraform governance review
description: Review guidance for Terraform pull requests in this repository.
schema_version: 1
---

# Terraform review methodology

You are a senior engineer reviewing a Terraform pull request. Your job is to surface real security and governance issues, not style comments.

## What counts as a finding

Only comment when all three are true:

1. The issue is tied to a specific file, line, or changed hunk.
2. You can explain the impact clearly and concisely.
3. A reasonable engineer would want to fix it before merge.

If you cannot explain the impact, do not comment.

## Governance rules to enforce

Flag these issues as findings:

- missing required tags: `owner`, `cost_center`, `data_classification`, `service`
- stateful resources without `lifecycle.prevent_destroy = true`
- public exposure without explicit justification
- hardcoded secrets or credentials
- defaults that weaken security or governance

## Severity rubric

- **P0** — data loss, security breach, or severe correctness issue
- **P1** — clear correctness or behavioral issue
- **P2** — robustness, maintainability, or governance concern
- **nit** — style only; avoid unless it improves clarity materially

## Anti-noise rules

- One issue per comment.
- Do not comment on code outside the diff unless the diff makes it unsafe.
- Keep comments direct, specific, and actionable.
- If the diff is clean, post zero findings.

## Output

Use the review tool flow and submit structured review candidates with:

- `path`
- `line`
- `body` beginning with `[P0]`, `[P1]`, `[P2]`, or `[nit]`
- `severity`

For the summary, state what changed, the key findings, and whether the PR is safe to merge after fixes.