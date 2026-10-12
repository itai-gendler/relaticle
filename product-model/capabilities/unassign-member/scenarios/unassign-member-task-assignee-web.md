---
kind: primary
routes:
  main: "Unassign member \u2014 task-assignee web"
steps:
- text: Choose the identity assignment change
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
- text: The Product saves the assignment change
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Assignees
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
---

# Unassign member — task-assignee web

## Trigger

The actor supplies an assignment change.

## Outcome

The specified Assignees assignment is removed without deleting the Account.
