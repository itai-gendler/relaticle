---
kind: validation
routes:
  main: Duplicate definition
steps:
- text: A field code conflicts with an existing definition for the record type.
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
  target: app/Actions/CustomFields/CreateCustomField.php
---

# Duplicate definition

## Trigger

A field code conflicts with an existing definition for the record type.

## Outcome

The duplicate definition is refused and no creation proposal is retained.
