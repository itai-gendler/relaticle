---
kind: primary
routes:
  main: Delete record — task rest
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: task
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/TasksController.php
---

# Delete record — task rest

## Trigger

The actor requests this task operation through rest.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain. REST returns 204.
