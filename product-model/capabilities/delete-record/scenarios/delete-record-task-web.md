---
kind: primary
routes:
  main: Delete record — task web
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: task
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
---

# Delete record — task web

## Trigger

The actor requests this task operation through web.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
