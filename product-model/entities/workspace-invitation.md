---
references:
- kind: code
  role: implementation
  target: app/Models/WorkspaceInvitation.php
domain: members
---

# Workspace Invitation

An individually addressable invitation for an email address and an assignable workspace role.

## Information kept

- **Email** — The retained email.
- **Role** — The retained assignable workspace role: Admin, Member or Viewer.
- **Inviter** — The retained inviter.
- **Workspace** — The workspace to which this instance belongs.
- **Issued At** — The retained issued at.
- **Expires At** — The retained expires at.
- **Invitation Credential** — The verifier of the opaque invitation credential; resending rotates it.

## States

### Issued

The workspace invitation is issued.
