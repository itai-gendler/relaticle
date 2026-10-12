---
kind: primary
routes:
  main: Permanently delete record — task web
steps:
- text: Confirm permanent removal of the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-admin
- text: The Product removes the record permanently
  kind: product
  entities:
  - entity: task
    effect: removes
    from: Deleted
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
---

# Permanently delete record — task web

## Trigger

The actor requests this task operation through web.

## Outcome

The record is no longer retained; independent linked records remain.
