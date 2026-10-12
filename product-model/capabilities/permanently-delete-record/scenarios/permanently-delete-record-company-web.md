---
kind: primary
routes:
  main: Permanently delete record — company web
steps:
- text: Confirm permanent removal of the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-admin
- text: The Product removes the record permanently
  kind: product
  entities:
  - entity: company
    effect: removes
    from: Deleted
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
---

# Permanently delete record — company web

## Trigger

The actor requests this company operation through web.

## Outcome

The record is no longer retained; independent linked records remain.
