---
kind: primary
routes:
  main: Edit record — task rest
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Title
    - Additional Values
    - Changed At
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

# Edit record — task rest

## Trigger

The actor requests this task operation through rest.

## Outcome

The supplied information is retained and omitted configured values remain.
