---
kind: primary
routes:
  main: Edit custom field
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
  - entity: custom-field-edit-proposal
    effect: creates
    facts:
    - Target Field
    - Earlier Definition Values
    - Proposed Definition Values
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
  target: packages/Chat/src/Tools/CustomField/UpdateCustomFieldTool.php
---

# Edit custom field

## Trigger

The actor requests the edit custom field operation.

## Outcome

The custom field edit proposal is retained with the desired definition or option plan. Fields, options and record values remain unchanged until its separate acceptance.
