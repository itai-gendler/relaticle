---
appliesTo:
- type: entity
  id: workspace-invitation
  effect: removes
permits:
- related:
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-owner
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-member
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
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

# Managers or matching recipients may remove invitations

Managers may revoke; the matching recipient may validly accept or decline. The owner’s deletion-scheduling cleanup removes pending invitations. Recipient grants require actual email equality and valid route/locked acceptance checks, never an invented recipient role.
