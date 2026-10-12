---
kind: primary
routes:
  main: Permanently delete record — person web
steps:
- text: Confirm permanent removal of the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-admin
- text: The Product removes the record permanently
  kind: product
  entities:
  - entity: person
    effect: removes
    from: Deleted
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Models/People.php
---

# Permanently delete record — person web

## Trigger

The actor requests this person operation through web.

## Outcome

The record is no longer retained; independent linked records remain.
