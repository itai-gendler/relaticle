---
appliesTo:
- type: entity
  id: person
  effect: changes
  facts: []
  to: Active
  contexts:
  - place: customer-web::workspace
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
  - verb: contains
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
references:
- kind: code
  role: implementation
  target: app/Policies/PeoplePolicy.php
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
---

# Workspace writers may restore the record — person

The grant follows this person’s Workspace: its owner through ownership, or its own Membership through the assigned role. Restoration returns a retained deleted record to Active.
