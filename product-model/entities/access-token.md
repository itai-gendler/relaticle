---
references:
- kind: code
  role: implementation
  target: app/Models/PersonalAccessToken.php
domain: access-tokens
---

# Access Token

A personal credential bound to an authorized Workspace and a clamped set of record-operation grants. The raw creation secret is revealed once and is not retained as a public fact.

## Information kept

- **Name** — The retained display name.
- **Owner** — The retained owner.
- **Workspace** — The workspace to which this instance belongs.
- **Read Grant** — The retained read grant.
- **Create Grant** — The retained create grant.
- **Update Grant** — The retained update grant.
- **Delete Grant** — The retained delete grant.
- **Created At** — When this instance was created.
- **Expires At** — The retained expires at.
- **Last Used At** — The retained last used at.
- **Credential Verifier** — The retained verifier, rather than the creation-only raw token secret.

## States

### Present

The access token is present.
