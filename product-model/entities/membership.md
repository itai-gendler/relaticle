---
references:
- kind: code
  role: implementation
  target: app/Models/Membership.php
domain: members
---

# Membership

One Account’s place and assigned Admin, Member or Viewer role in a particular Workspace.

## Information kept

- **Account** — The retained account.
- **Workspace** — The workspace to which this instance belongs.
- **Role** — The retained assignable workspace role: Admin, Member or Viewer.

## States

### Active

The instance is available in its ordinary workspace context.
