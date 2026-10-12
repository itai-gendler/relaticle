---
kind: primary
routes:
  main: Restore record — company web
steps:
- text: Choose Restore for the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-member
- text: The Product restores the retained record
  kind: product
  entities:
  - entity: company
    effect: changes
    facts: []
    from: Deleted
    to: Active
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
---

# Restore record — company web

## Trigger

The actor requests this company operation through web.

## Outcome

The record returns to ordinary workspace reads.
