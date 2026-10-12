---
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
---

# Opportunity

A sale in progress. Company and Point of Contact are optional independently checked links; the person need not belong to the selected Company.

## Information kept

- **Name** — The retained display name.
- **Company** — The optional linked Company.
- **Point of Contact** — The optional independently linked Person.
- **Stage** — The configured opportunity pipeline value.
- **Amount** — The retained amount.
- **Close Date** — The closing calendar date, without datetime conversion.
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
