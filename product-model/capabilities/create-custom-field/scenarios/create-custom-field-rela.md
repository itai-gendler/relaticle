---
kind: primary
routes:
  main: Create custom field
steps:
- text: Supply the desired common definition or option change
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product validates the plan and retains the proposal
  kind: product
  entities:
  - entity: custom-field-creation-proposal
    effect: creates
    facts:
    - Proposed Name
    - Proposed Code
    - Proposed Record Type
    - Proposed Field Type
    - Proposed Options
    - Requester
    - Workspace
    - Conversation
    - Turn
    - Valid Until
    - Decision
    - Decision Time
    - Dependencies
    - Results
    to: Proposed
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/CustomField/CreateCustomFieldTool.php
---

# Create custom field

## Trigger

The actor requests the create custom field operation.

## Outcome

The custom field creation proposal is retained with the desired definition or option plan. Fields, options and record values remain unchanged until its separate acceptance.
