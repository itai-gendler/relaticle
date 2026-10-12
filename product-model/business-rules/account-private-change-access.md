---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts:
  - Current Workspace
  - Task Assignment In-app
  - Task Assignment Email
  - Task Digest Email
permits:
- related:
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: has identity
    entity: workspace-member
- related:
  - verb: has identity
    entity: workspace-viewer
- related:
  - verb: holds
    entity: membership
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: holds
    entity: membership
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

# Accounts may change their own selection and notification preferences

Self selection requires target-workspace membership. Notification preferences belong to the acting Account. Administrative removal can clear the addressed Account’s matching selection; acceptance primes the joined tenant.
