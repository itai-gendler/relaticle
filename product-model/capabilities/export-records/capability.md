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

# Export records

Select CRM information and obtain a generated export, using the acting Account’s timezone for datetimes.
