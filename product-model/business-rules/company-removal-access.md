---
appliesTo:
- type: entity
  id: company
  effect: removes
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
references:
- kind: code
  role: implementation
  target: app/Policies/CompanyPolicy.php
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
---

# Owners and admins may permanently remove the record — company

The grant follows this company’s Workspace: its owner through ownership, or its own Membership through the assigned role. Permanent removal uses Records Force Delete; ordinary Members do not receive it.
