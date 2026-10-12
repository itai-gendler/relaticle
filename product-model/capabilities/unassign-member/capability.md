---
availability:
- place: customer-web::workspace
- place: rest-api
- place: agent-access
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

# Unassign a member

Clear a Company’s Account Owner or detach Task Assignees; dedicated detachment can remove former workspace members.
