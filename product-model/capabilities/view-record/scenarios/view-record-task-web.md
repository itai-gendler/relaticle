---
kind: primary
routes:
  main: View record — task web
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
- text: The Product shows the selected Task form values and linked selections
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
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource.php
- kind: code
  role: implementation
  target: app/Policies/TaskPolicy.php#update
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource/Forms/TaskForm.php#get
---

# View record — task web

## Trigger

The person opens the selected Task through its native edit control.

## Outcome

The selected Task editor presents its own form values and linked selections without changing the record. Collection, REST, MCP and Rela reads retain their separate disclosure contracts.
