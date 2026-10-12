---
kind: primary
routes:
  main: Delete record — note mcp
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::note
  actor: ai-agent
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: note
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: agent-access::note
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseDeleteTool.php
---

# Delete record — note mcp

## Trigger

The actor requests this note operation through mcp.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
