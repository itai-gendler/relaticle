---
kind: primary
routes:
  main: Permanently delete record — note web
steps:
- text: Confirm permanent removal of the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-admin
- text: The Product removes the record permanently
  kind: product
  entities:
  - entity: note
    effect: removes
    from: Deleted
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
---

# Permanently delete record — note web

## Trigger

The actor requests this note operation through web.

## Outcome

The record is no longer retained; independent linked records remain.
