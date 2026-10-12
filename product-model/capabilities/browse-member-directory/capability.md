---
availability:
- place: customer-web::workspace
- place: agent-access
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/WhoAmiTool.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/ListWorkspaceMembersTool.php
---

# Browse member directory

Discover member names and emails through Rela or MCP, distinct from the administrative roster.
