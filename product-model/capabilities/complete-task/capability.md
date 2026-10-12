---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: app/Actions/Opportunity/UpdateOpportunity.php
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
- kind: code
  role: implementation
  target: app/Queries/Concerns/ListsEntity.php
---

# Complete a Task

Mark a Task complete from Home with the workspace Status option named Done; missing Done has its observed refusal.
