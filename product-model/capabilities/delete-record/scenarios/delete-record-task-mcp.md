---
kind: primary
routes:
  main: Delete record — task mcp
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: task
    effect: changes
    facts: []
    from: Active
    to: Deleted
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
  target: app/Mcp/Tools/BaseDeleteTool.php
---

# Delete record — task mcp

## Trigger

The actor requests this task operation through mcp.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
