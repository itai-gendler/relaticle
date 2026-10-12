---
appliesTo:
- type: entity
  id: workspace
  effect: changes
  facts:
  - Scheduled Deletion
  to: Active
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

# Only the owner cancels workspace deletion

The owner can clear an existing schedule; this does not grant financial subscription restoration.
