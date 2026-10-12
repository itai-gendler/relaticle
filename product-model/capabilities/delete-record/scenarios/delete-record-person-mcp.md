---
kind: primary
routes:
  main: Delete record — person mcp
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: person
    effect: changes
    facts: []
    from: Active
    to: Deleted
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
  target: app/Mcp/Tools/BaseDeleteTool.php
---

# Delete record — person mcp

## Trigger

The actor requests this person operation through mcp.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
