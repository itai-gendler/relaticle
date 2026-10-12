---
appliesTo:
- type: entity
  id: custom-field-option
  effect: creates
  to: Present
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

# Owners and admins may add field options

Independent option addition uses Fields Manage. Initial options created with a new Field are dependent creations. The owner’s no-Opportunity setup preset also creates the target workspace stage options.
