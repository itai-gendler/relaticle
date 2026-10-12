---
entities:
- entity: account
  shows:
  - Name
  - Email
- entity: workspace
  shows:
  - Name
- entity: membership
  shows:
  - Role
- entity: access-token
  shows:
  - Read Grant
  - Create Grant
  - Update Grant
  - Delete Grant
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/WhoAmiTool.php
---

# Account context

Own identity and current workspace/role capabilities, member names and emails, and abilities of the actual credential.
