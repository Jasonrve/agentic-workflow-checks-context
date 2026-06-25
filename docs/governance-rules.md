# Governance rules

The AI reviewer should flag any Terraform change that violates these rules, even if normal tooling passes.

## Required tags

Every managed resource must include these tags:

- `owner`
- `cost_center`
- `data_classification`
- `service`

## Tag expectations

- `owner` must identify a person or team responsible for the resource
- `data_classification` must be one of: `public`, `internal`, `confidential`, `restricted`

## Stateful resources

Stateful resources should use `lifecycle { prevent_destroy = true }` unless a clear exception is documented.

## Security posture

- no public exposure without explicit justification
- no hardcoded secrets
- least privilege by default

## Review behavior

If a required tag is missing, treat it as a **high severity governance issue**.
