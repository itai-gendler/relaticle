---
kind: primary
routes:
  main: Delete record — opportunity mcp
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts: []
    from: Active
    to: Deleted
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
  target: app/Mcp/Tools/BaseDeleteTool.php
---

# Delete record — opportunity mcp

## Trigger

The actor requests this opportunity operation through mcp.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain.
