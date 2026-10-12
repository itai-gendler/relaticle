---
entities:
- entity: workspace
  shows:
  - Name
- entity: workspace-invitation
  shows:
  - Email
  - Role
  - Workspace
  - Expires At
references:
- kind: code
  role: implementation
  target: app/Http/Controllers/AcceptWorkspaceInvitationController.php
---

# Invitation acceptance

The addressed invitation’s confirmation, validity and acceptance result.
