---
kind: validation
routes:
  main: Foreign selected record
steps:
- text: The selected identifier is outside the resolved working scope.
  kind: condition
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Foreign selected record

## Trigger

The selected identifier is outside the resolved workspace.

## Outcome

The selected request returns not found or the traced refusal without disclosing the foreign record.
