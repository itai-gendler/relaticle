---
kind: primary
routes:
  record: Create in Tasks
  home: Create from Home
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    record:
      place: customer-web::workspace::task
    home:
      place: customer-web::workspace::home
  actor: workspace-member
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: task
    effect: creates
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
    - Order
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  contexts:
    record:
      place: customer-web::workspace::task
    home:
      place: customer-web::workspace::home
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: app/Filament/Pages/Dashboard.php
- kind: code
  role: implementation
  target: app/Filament/Actions/CreateTaskAction.php
---

# Create record — task web

## Trigger

The actor requests this task operation through web.

## Outcome

A new active Task is retained and returned. The native creation hook attempts assignment notifications for the submitted assignees according to their preferences.
