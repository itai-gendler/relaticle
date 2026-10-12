---
appliesTo:
- type: entity
  id: opportunity
  effect: reads
  contexts:
  - place: customer-web::workspace::export-records
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
  target: app/Policies/OpportunityPolicy.php
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
---

# Export-authorized members may export record facts — opportunity

The grant follows this opportunity’s Workspace: its owner through ownership, or its own Membership through the assigned role. Data Export is held by Owner, Admin and Member. This additional read selector closes export disclosure for Viewer.
