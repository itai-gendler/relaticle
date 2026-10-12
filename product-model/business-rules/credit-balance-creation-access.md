---
appliesTo:
- type: entity
  id: credit-balance
  effect: creates
  to: Available
permits:
- unattended: true
- related:
  - verb: has balance
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: has balance
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
  - verb: has balance
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  when:
  - entity: membership
    fact: Role
    is: Member
- related:
  - verb: has balance
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when:
  - entity: membership
    fact: Role
    is: Viewer
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/CreditService.php
---

# The Product initializes a workspace credit balance

Workspace creation initializes the dependent balance. Inspected lazy recovery initializes the workspace allocation without granting purchase authority.
