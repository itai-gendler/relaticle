---
entities:
- entity: account
  shows:
  - Name
  - Email
- entity: membership
  shows:
  - Role
  collects:
  - Role
- entity: workspace-invitation
  shows:
  - Email
  - Role
  - Issued At
  - Expires At
  collects:
  - Email
  - Role
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Workspace/Members.php
---

# Members

The administrative roster and outgoing invitations for one workspace.
