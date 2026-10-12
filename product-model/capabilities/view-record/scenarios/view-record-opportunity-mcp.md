---
kind: primary
routes:
  main: View record — opportunity mcp
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: opportunity
    effect: reads
    facts:
    - Name
    - Company
    - Point of Contact
    - Stage
    - Amount
    - Close Date
    - Additional Values
    - Creator
    - Creation Source
    - Created At
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
  target: app/Mcp/Tools/BaseShowTool.php
---

# View record — opportunity mcp

## Trigger

The actor requests this opportunity operation through mcp.

## Outcome

The selected record is returned under this transport’s disclosure contract. Allowed related collections return at most 25 newest items with returned/total/truncated metadata; unknown includes are ignored.
