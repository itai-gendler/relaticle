---
kind: primary
routes:
  main: Restore record — task web
steps:
- text: Choose Restore for the deleted record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
- text: The Product restores the retained record
  kind: product
  entities:
  - entity: task
    effect: changes
    facts: []
    from: Deleted
    to: Active
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
---

# Restore record — task web

## Trigger

The actor requests this task operation through web.

## Outcome

The record returns to ordinary workspace reads.
