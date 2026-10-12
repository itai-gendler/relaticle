---
appliesTo:
- type: entity
  id: workspace
  effect: changes
  facts:
  - Use Case
  - Use Case Context
  - Setup Step
  - Other Use Case
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

# Only the workspace owner completes setup

The target owner and current pending setup step are checked and locked; settled setup is not replayed.
