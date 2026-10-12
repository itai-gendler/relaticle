---
kind: primary
routes:
  main: Edit record — opportunity mcp
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts:
    - Name
    - Additional Values
    - Changed At
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseUpdateTool.php
---

# Edit record — opportunity mcp

## Trigger

The actor requests this opportunity operation through mcp.

## Outcome

The supplied information is retained and omitted configured values remain.
