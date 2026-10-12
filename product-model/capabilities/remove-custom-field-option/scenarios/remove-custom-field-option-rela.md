---
kind: primary
routes:
  main: Remove custom field option
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
  - entity: custom-field-options-proposal
    effect: creates
    facts:
    - Target Field
    - Current Options
    - Desired Options
    - Desired Order
    - Removal Replacement Plan
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
  target: packages/Chat/src/Tools/CustomField/SetCustomFieldOptionsTool.php
---

# Remove custom field option

## Trigger

The actor requests the remove custom field option operation.

## Outcome

The custom field options proposal is retained with the desired definition or option plan. Fields, options and record values remain unchanged until its separate acceptance.
