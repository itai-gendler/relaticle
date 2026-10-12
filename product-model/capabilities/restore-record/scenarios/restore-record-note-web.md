---
kind: primary
routes:
  main: Restore record — note web
steps:
- text: Choose Restore for the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
- text: The Product restores the retained record
  kind: product
  entities:
  - entity: note
    effect: changes
    facts: []
    from: Deleted
    to: Active
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
---

# Restore record — note web

## Trigger

The actor requests this note operation through web.

## Outcome

The record returns to ordinary workspace reads.
