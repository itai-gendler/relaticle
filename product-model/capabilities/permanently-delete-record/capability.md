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

# Permanently delete a record

Permanently remove a soft-deleted CRM record through customer web, preserving independent linked records.
