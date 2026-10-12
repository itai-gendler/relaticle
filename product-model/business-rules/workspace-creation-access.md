---
appliesTo:
- type: entity
  id: workspace
  effect: creates
  to: Active
permits:
- actors:
  - workspace-owner
  when:
  - entity: product-configuration
    fact: Maximum Owned Workspaces
    over: 0
- actors:
  - workspace-admin
  when:
  - entity: product-configuration
    fact: Maximum Owned Workspaces
    over: 0
- actors:
  - workspace-member
  when:
  - entity: product-configuration
    fact: Maximum Owned Workspaces
    over: 0
- actors:
  - workspace-viewer
  when:
  - entity: product-configuration
    fact: Maximum Owned Workspaces
    over: 0
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

# Signed-in Accounts may create within the ownership limit

The actual Account owned-workspace relation count must be below Maximum Owned Workspaces, default ten, including scheduled deletions. Invited memberships do not count. The count is computed from the Account’s owned-workspace relation.
