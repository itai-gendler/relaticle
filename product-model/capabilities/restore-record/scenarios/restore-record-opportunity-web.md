---
kind: primary
routes:
  main: Restore record — opportunity web
steps:
- text: Choose Restore for the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
- text: The Product restores the retained record
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts: []
    from: Deleted
    to: Active
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
---

# Restore record — opportunity web

## Trigger

The actor requests this opportunity operation through web.

## Outcome

The record returns to ordinary workspace reads.
