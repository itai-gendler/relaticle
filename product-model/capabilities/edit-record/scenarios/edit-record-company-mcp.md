---
kind: primary
routes:
  main: Edit record — company mcp
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::company
  actor: ai-agent
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: company
    effect: changes
    facts:
    - Name
    - Additional Values
    - Changed At
  contexts:
    main:
      place: agent-access::company
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseUpdateTool.php
---

# Edit record — company mcp

## Trigger

The actor requests this company operation through mcp.

## Outcome

The supplied information is retained and omitted configured values remain.
