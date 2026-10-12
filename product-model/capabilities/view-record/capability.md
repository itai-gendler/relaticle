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

# View a record

Open one workspace CRM record. Each transport publishes its own facts and related-record expansion; unknown includes have distinct REST, MCP and Rela outcomes.
