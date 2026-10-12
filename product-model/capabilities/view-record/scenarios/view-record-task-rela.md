---
kind: primary
routes:
  main: View record — task rela
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product returns the requested CRM results and emits their display block unless lookup was requested
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
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseReadShowTool.php
---

# View record — task rela

## Trigger

The actor requests this task operation through rela.

## Outcome

The selected record is returned under this transport’s disclosure contract. Selected related collections contain at most ten newest items with true totals; unknown includes return an error. Note body remains directly available, while related free text is stripped and capped.
