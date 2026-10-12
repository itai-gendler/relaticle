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
- entity: company
  shows:
  - Name
- entity: person
  shows:
  - Name
- entity: opportunity
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource.php
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource/Forms/TaskForm.php#get
---

# Task

Current form values and linked selections for one selected Task.
