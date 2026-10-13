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
---

# Set up a Workspace

Complete inspected setup (a mailbox and its sharing level first where Email Integration is enabled, then the use case and optional invitations) and reach the configured Home or personal setup Chat.
