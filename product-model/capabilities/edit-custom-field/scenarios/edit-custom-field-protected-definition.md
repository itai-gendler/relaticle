---
kind: validation
routes:
  main: Protected definition
steps:
- text: The request changes a protected system-defined name or deactivates its definition.
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
  target: app/Actions/CustomFields/UpdateCustomField.php
---

# Protected definition

## Trigger

The request changes a protected system-defined name or deactivates its definition.

## Outcome

The protected change is refused and the definition remains.
