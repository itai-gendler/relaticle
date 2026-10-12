---
kind: primary
routes:
  main: View record — company mcp
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::company
  actor: ai-agent
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
    - Account Owner
    - Domains
    - ICP
    - LinkedIn
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
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
  target: app/Mcp/Tools/BaseShowTool.php
---

# View record — company mcp

## Trigger

The actor requests this company operation through mcp.

## Outcome

The selected record is returned under this transport’s disclosure contract. Allowed related collections return at most 25 newest items with returned/total/truncated metadata; unknown includes are ignored.
