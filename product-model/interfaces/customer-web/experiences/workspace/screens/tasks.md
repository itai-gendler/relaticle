---
entities:
- entity: task
  shows:
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
  - Order
  collects:
  - Order
  - Status
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource.php
---

# Tasks

The workspace collection of Tasks. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
