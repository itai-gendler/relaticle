---
appliesTo:
- type: entity
  id: access-token
  facts:
  - Workspace
  - Read Grant
  - Create Grant
  - Update Grant
  - Delete Grant
- type: context
  context:
    place: rest-api
- type: context
  context:
    place: agent-access
references:
- kind: code
  role: implementation
  target: app/Http/Middleware/SetApiWorkspaceContext.php
- kind: code
  role: implementation
  target: app/Http/Middleware/EnsureTokenHasAbility.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/Concerns/ChecksTokenAbility.php
---

# The actual credential selects API Workspace without saving web selection

A bound personal/OAuth credential is authoritative despite a conflicting header. Passport without a pinned workspace is invalid. Legacy unbound personal tokens use a valid workspace header or current Account selection, still requiring membership. Binding sets the acting user’s workspace in memory, restores context and does not persist web selection. The selected REST token must carry the actual operation ability; Passport cookie tokens are refused. MCP OAuth needs mcp:use; personal MCP tokens need the operation ability. Any other owned token is irrelevant.
