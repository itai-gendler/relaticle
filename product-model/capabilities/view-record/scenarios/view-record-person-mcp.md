---
kind: primary
routes:
  main: View record — person mcp
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: person
    effect: reads
    facts:
    - Name
    - Company
    - Emails
    - Phone Numbers
    - Job Title
    - LinkedIn
    - Additional Values
    - Creator
    - Creation Source
    - Created At
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
  target: app/Mcp/Tools/BaseShowTool.php
---

# View record — person mcp

## Trigger

The actor requests this person operation through mcp.

## Outcome

The selected record is returned under this transport’s disclosure contract. Allowed related collections return at most 25 newest items with returned/total/truncated metadata; unknown includes are ignored.
