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

# Create a record

Create a CRM record with its own information, configured values and optional links. Rela retains a creation proposal first; accepting it creates the record.
