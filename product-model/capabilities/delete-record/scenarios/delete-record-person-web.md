---
kind: primary
routes:
  main: Delete record — person web
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: person
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/People.php
---

# Delete record — person web

## Trigger

The actor requests this person operation through web.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
