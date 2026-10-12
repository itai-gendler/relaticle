---
appliesTo:
- type: entity
  id: custom-field-option
  effect: reads
permits:
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
  - verb: connects
    entity: ai-agent
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when: &id001
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  - verb: connects
    entity: ai-agent
  when: *id001
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  when: &id002
  - entity: membership
    fact: Role
    is: Member
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  - verb: connects
    entity: ai-agent
  when: *id002
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when: &id003
  - entity: membership
    fact: Role
    is: Viewer
- related:
  - verb: has options
    entity: custom-field
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  - verb: connects
    entity: ai-agent
  when: *id003
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: app/Actions/CustomFields/UpdateCustomField.php
- kind: code
  role: implementation
  target: app/Actions/CustomFields/SetCustomFieldOptions.php
---

# Workspace members may read field options

Options inherit their definition’s workspace discovery scope. On REST token-bearing requests the actual selected credential must hold the corresponding read/create/update/delete ability; Passport cookie credentials are refused. On MCP OAuth the selected credential must hold mcp:use, while personal tokens require the operation ability. Session-only REST calls follow their inspected policy path. Ownership of some other credential never qualifies the request.
