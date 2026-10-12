---
availability:
- place: customer-web::workspace
- place: rest-api
- place: agent-access
references:
- kind: code
  role: implementation
  target: app/Actions/CustomFields/CreateCustomField.php
- kind: code
  role: implementation
  target: app/Actions/CustomFields/SetCustomFieldOptions.php
---

# Browse Custom Fields

Discover field definitions and options. REST returns active definitions; MCP and Rela can describe inactive definitions too.
