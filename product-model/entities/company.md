---
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
relations:
- entity: person
  verb: has people
  cardinality: one-to-many
- entity: opportunity
  verb: has opportunities
  cardinality: one-to-many
---

# Company

A business the workspace tracks. Its Account Owner is a workspace user, distinct from a related CRM Person.

## Information kept

- **Name** — The retained display name.
- **Account Owner** — The assigned workspace Account responsible for this Company.
- **Domains** — The retained domains.
- **ICP** — The retained icp.
- **LinkedIn** — The retained linkedin.
- **Additional Values** — Other configured values, excluding facts explicitly named here.
- **Workspace** — The workspace to which this instance belongs.
- **Creator** — The Account that created the CRM record.
- **Creation Source** — The recorded origin of the CRM creation.
- **Created At** — When this instance was created.
- **Changed At** — When this instance was last changed.

## States

### Active

The instance is available in its ordinary workspace context.

### Deleted

The CRM record is soft-deleted and retained for restoration or permanent removal.
