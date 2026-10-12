---
references:
- kind: code
  role: implementation
  target: app/Models/People.php
relations:
- entity: opportunity
  verb: is point of contact for
  cardinality: one-to-many
---

# Person

A human the workspace tracks, optionally linked to a Company. A CRM Person is distinct from a signed-in Account.

## Information kept

- **Name** — The retained display name.
- **Company** — The optional linked Company.
- **Emails** — The retained emails.
- **Phone Numbers** — The retained phone numbers.
- **Job Title** — The retained job title.
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
