---
kind: validation
routes:
  main: Done protected
steps:
- text: The plan renames the existing assigned work Status Done option.
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

# Done protected

## Trigger

The plan renames the existing Task Status Done option.

## Outcome

The plan is refused; the Done option identity and name remain.
