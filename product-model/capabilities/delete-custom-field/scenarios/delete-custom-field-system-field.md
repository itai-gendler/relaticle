---
kind: validation
routes:
  main: System field
steps:
- text: The selected field is system-defined.
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

# System field

## Trigger

The selected field is system-defined.

## Outcome

The removal is refused and the system definition remains.
