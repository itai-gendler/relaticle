---
kind: primary
routes:
  main: Create record — person mcp
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: person
    effect: creates
    facts:
    - Name
    - Company
    - Emails
    - Phone Numbers
    - Job Title
    - LinkedIn
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
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
  target: app/Mcp/Tools/BaseCreateTool.php
---

# Create record — person mcp

## Trigger

The actor requests this person operation through mcp.

## Outcome

A new active person is retained and returned.
