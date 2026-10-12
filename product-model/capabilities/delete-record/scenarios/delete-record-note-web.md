---
kind: primary
routes:
  main: Delete record — note web
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: note
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
---

# Delete record — note web

## Trigger

The actor requests this note operation through web.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
