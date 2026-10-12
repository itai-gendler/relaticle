---
kind: primary
routes:
  main: Permanently delete record — opportunity web
steps:
- text: Confirm permanent removal of the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-admin
- text: The Product removes the record permanently
  kind: product
  entities:
  - entity: opportunity
    effect: removes
    from: Deleted
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
---

# Permanently delete record — opportunity web

## Trigger

The actor requests this opportunity operation through web.

## Outcome

The record is no longer retained; independent linked records remain.
