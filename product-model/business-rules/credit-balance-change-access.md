---
appliesTo:
- type: entity
  id: credit-balance
  effect: changes
  facts:
  - Remaining
  - Used
permits:
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

# A workspace request may reserve and resolve its credits

Request-attributed generation reserves and settles/refunds its own credit usage through the atomic idempotent accounting path. This does not authorize arbitrary credit adjustment or purchases.
