---
kind: primary
routes:
  main: Link records — task-opportunity rest
steps:
- text: Choose the relationship entries to link
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Opportunities
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

# Link records — task-opportunity rest

## Trigger

The actor supplies a relationship change.

## Outcome

The requested entries are linked; dedicated attachment retains existing entries while supplied edit collections replace them.
