---
actors:
- workspace-admin
- workspace-member
- workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Http/Controllers/AcceptWorkspaceInvitationController.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/PendingInvitationsForUser.php
---

# Join an invited Workspace

## Goal

Use an addressed invitation to join the Workspace and begin reading its Tasks.

## Success criterion

The same Account has the issued role, the joined Workspace is its persisted selection, its customer tenant is primed, and its Task collection can be browsed.
