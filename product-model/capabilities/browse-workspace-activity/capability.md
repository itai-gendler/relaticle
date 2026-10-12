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

# Browse workspace activity

Read activity across workspace records or a record type, including import summaries; cross-record queries retain Activity View authorization.
