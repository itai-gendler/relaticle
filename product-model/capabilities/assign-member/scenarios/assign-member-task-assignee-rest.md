---
kind: primary
routes:
  main: "Assign member \u2014 task-assignee rest"
steps:
- text: Choose the identity assignment change
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
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
      place: rest-api::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
---

# Assign member — task-assignee rest

## Trigger

The actor supplies an assignment change.

## Outcome

The specified Assignees assignment is retained. Traced actions notify only newly attached assignees according to preferences; native save notification parity is not established.
