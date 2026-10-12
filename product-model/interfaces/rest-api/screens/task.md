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
  collects:
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
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/TaskResource.php
---

# Task

One selected task with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
