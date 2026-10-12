---
appliesTo:
- type: entity
  id: note
  effect: reads
  contexts:
  - place: customer-web::workspace::note
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
  target: app/Filament/Resources/NoteResource.php
- kind: code
  role: implementation
  target: app/Policies/NotePolicy.php#update
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php#capabilities
---

# Workspace writers may open the selected Note editor

The native selected Note context is reached through its edit control, which requires update authority for that record. The owner of its Workspace or its own Admin or Member Membership qualifies. Viewer record-view authority alone does not open this editor. This entry restriction does not restrict collection, REST, MCP or Rela reads. The separate record-read Rule and workspace boundary remain applicable.
