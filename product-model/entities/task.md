---
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
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

# Task

Follow-up work with configurable Status and Priority, a Due Date, user Assignees and independent links to CRM records.

## Information kept

- **Title** — The retained title.
- **Status** — The configured task status value.
- **Priority** — The configured task priority value.
- **Due Date** — The UTC due datetime, presented in the applicable account timezone.
- **Description** — The retained description.
- **Assignees** — The workspace Accounts assigned to this work.
- **Companies** — The independent linked Companies.
- **People** — The independent linked People.
- **Opportunities** — The independent linked Opportunities.
- **Order** — The retained position used by the applicable board or option ordering.
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
