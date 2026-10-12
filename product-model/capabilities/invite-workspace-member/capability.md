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

# Invite a workspace member

Issue or resend an addressed invitation; Rela retains a proposal requiring its own acceptance.
