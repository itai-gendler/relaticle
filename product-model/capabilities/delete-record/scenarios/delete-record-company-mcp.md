---
kind: primary
routes:
  main: Delete record — company mcp
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::company
  actor: ai-agent
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: company
    effect: changes
    facts: []
    from: Active
    to: Deleted
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
  target: app/Mcp/Tools/BaseDeleteTool.php
---

# Delete record — company mcp

## Trigger

The actor requests this company operation through mcp.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
