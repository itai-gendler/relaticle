---
appliesTo:
- type: entity
  id: custom-field-option
  effect: changes
  facts:
  - Name
  - Order
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
  target: app/Actions/CustomFields/UpdateCustomField.php
- kind: code
  role: implementation
  target: app/Actions/CustomFields/SetCustomFieldOptions.php
---

# Owners and admins may change field options

Fields Manage governs option names and ordering; used-value and Done protections remain.
