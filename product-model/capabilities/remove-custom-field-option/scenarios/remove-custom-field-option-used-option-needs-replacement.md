---
kind: validation
routes:
  main: Used option needs replacement
steps:
- text: The option being removed has retained values and the plan names no replacement.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Actions/CustomFields/SetCustomFieldOptions.php
---

# Used option needs replacement

## Trigger

The option being removed has retained values and the plan names no replacement.

## Outcome

The plan is refused; a used option needs an explicit valid replacement, including values of soft-deleted records.
