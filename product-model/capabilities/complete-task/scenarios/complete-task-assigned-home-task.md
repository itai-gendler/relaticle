---
kind: primary
routes:
  main: Complete assigned Home Task
steps:
- text: Choose Mark complete
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-member
- text: The Product sets the working scope Done option
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Status
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/CompleteTask.php
---

# Complete assigned Home Task

## Trigger

Home offers an assigned open Task.

## Outcome

Status becomes the workspace option named Done.
