---
kind: validation
routes:
  main: Active valued field
steps:
- text: The selected active field has retained record values.
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
  target: app/Actions/CustomFields/DeleteCustomField.php
---

# Active valued field

## Trigger

The selected active field has retained record values.

## Outcome

Removal is refused until the field is deactivated; values remain.
