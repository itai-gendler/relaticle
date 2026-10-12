---
kind: primary
routes:
  main: "Discover member directory \u2014 mcp"
steps:
- text: Request the member directory
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::account-context
  actor: ai-agent
- text: The Product returns the working scope name and email directory
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - Email
  contexts:
    main:
      place: agent-access::account-context
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/WhoAmiTool.php
---

# Discover member directory — mcp

## Trigger

The actor requests workspace member names and email addresses.

## Outcome

The names and emails are returned. MCP Get Account Context includes the workspace member directory.
