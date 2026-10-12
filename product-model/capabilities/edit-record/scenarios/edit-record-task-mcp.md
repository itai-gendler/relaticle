---
kind: primary
routes:
  main: Edit record — task mcp
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Title
    - Additional Values
    - Changed At
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseUpdateTool.php
---

# Edit record — task mcp

## Trigger

The actor requests this task operation through mcp.

## Outcome

The supplied information is retained and omitted configured values remain.
