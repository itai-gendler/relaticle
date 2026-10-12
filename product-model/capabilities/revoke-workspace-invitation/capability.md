---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/CreateWorkspace.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/WorkspaceMembers.php
domain: members
---

# Revoke a workspace invitation

Remove an outgoing invitation so its credential no longer joins the workspace.
