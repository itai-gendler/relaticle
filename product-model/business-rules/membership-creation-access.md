---
appliesTo:
- type: entity
  id: membership
  effect: creates
  to: Active
permits:
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-owner
  when:
  - entity: account
    fact: Email Verified
    is: true
  - entity: account
    fact: Scheduled Deletion
    absent: true
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - entity: account
    fact: Email Verified
    is: true
  - entity: account
    fact: Scheduled Deletion
    absent: true
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  when:
  - entity: account
    fact: Email Verified
    is: true
  - entity: account
    fact: Scheduled Deletion
    absent: true
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when:
  - entity: account
    fact: Email Verified
    is: true
  - entity: account
    fact: Scheduled Deletion
    absent: true
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

# A matching invitation recipient may acquire its issued role

Creation requires a valid addressed invitation, verified signed-in identity with canonical email match, no Account/Workspace deletion schedule, and the locked unexpired/unrevoked check. The workspace owner’s authorized adder supplies the recorded assignable role. It is not arbitrary membership creation.
