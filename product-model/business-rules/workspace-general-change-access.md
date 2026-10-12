---
appliesTo:
- type: entity
  id: workspace
  effect: changes
  facts:
  - Name
  - Handle
  - Logo
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

# Only the workspace owner changes General settings

Workspace Manage is owner-only and follows the target Workspace’s owner. Handle validation remains.
