---
appliesTo:
- type: entity
  id: workspace
  effect: changes
  facts:
  - Scheduled Deletion
  to: Scheduled for Deletion
permits:
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
---

# Only the owner schedules a nonpersonal workspace deletion

The target workspace must not be personal. The schedule is retained before best-effort subscription cancellation.
