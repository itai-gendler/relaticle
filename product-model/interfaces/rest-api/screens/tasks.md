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
  - Creator
  - Creation Source
  - Created At
  - Changed At
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/TaskResource.php
---

# Tasks

The workspace collection of Tasks. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
