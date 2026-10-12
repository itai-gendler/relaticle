---
kind: primary
routes:
  main: Restore record — person web
steps:
- text: Choose Restore for the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-member
- text: The Product restores the retained record
  kind: product
  entities:
  - entity: person
    effect: changes
    facts: []
    from: Deleted
    to: Active
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/People.php
---

# Restore record — person web

## Trigger

The actor requests this person operation through web.

## Outcome

The record returns to ordinary workspace reads.
