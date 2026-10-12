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

# Browse records

Browse workspace Companies, People, Opportunities, Tasks or Notes using the applicable filters, sort, search, paging and boards. Rela reads use the shared list query and their own bounded result presentation.
