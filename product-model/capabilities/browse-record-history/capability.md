---
availability:
- place: customer-web::workspace
- place: agent-access
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListActivityTool.php
---

# Browse record history

Read one visible CRM subject’s change history; Rela and MCP group complete saves and keep their own result limits.
