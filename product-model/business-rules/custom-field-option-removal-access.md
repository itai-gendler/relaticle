---
appliesTo:
- type: entity
  id: custom-field-option
  effect: removes
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

# Owners and admins may remove field options

Independent removal requires Fields Manage and a valid replacement plan for used values. The owner’s no-Opportunity setup preset replaces the target stage option list when no Opportunities, including deleted ones, exist.
