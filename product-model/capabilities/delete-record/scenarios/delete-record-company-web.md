---
kind: primary
routes:
  main: Delete record — company web
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: company
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
---

# Delete record — company web

## Trigger

The actor requests this company operation through web.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
