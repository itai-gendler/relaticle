---
kind: primary
routes:
  main: View record — task rest
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-viewer
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Status
    - Priority
    - Due Date
    - Description
    - Assignees
    - Companies
    - People
    - Opportunities
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: rest-api::task
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/TasksController.php
---

# View record — task rest

## Trigger

The actor requests this task operation through rest.

## Outcome

The selected record is returned under this transport’s disclosure contract. The controller loads configured values and does not process arbitrary selected-record includes.
