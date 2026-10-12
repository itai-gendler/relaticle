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

# Remove a member

Remove an addressed Membership while preserving owner and peer-Admin protections.
