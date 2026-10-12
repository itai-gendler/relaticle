---
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
relations:
- entity: company
  verb: links
  cardinality: many-to-many
- entity: person
  verb: links
  cardinality: many-to-many
- entity: opportunity
  verb: links
  cardinality: many-to-many
---

# Note

A titled body of workspace information, independently linked to Companies, People and Opportunities.

## Information kept

- **Title** — The retained title.
- **Body** — The retained body.
- **Companies** — The independent linked Companies.
- **People** — The independent linked People.
- **Opportunities** — The independent linked Opportunities.
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
