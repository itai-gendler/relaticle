---
kind: primary
routes:
  main: Edit record — person mcp
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: person
    effect: changes
    facts:
    - Name
    - Additional Values
    - Changed At
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/People.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseUpdateTool.php
---

# Edit record — person mcp

## Trigger

The actor requests this person operation through mcp.

## Outcome

The supplied information is retained and omitted configured values remain.
