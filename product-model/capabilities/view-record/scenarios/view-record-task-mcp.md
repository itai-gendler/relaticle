---
kind: primary
routes:
  main: View record — task mcp
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Status
    - Priority
    - Due Date
    - Description
    - Assignees
    - Companies
    - People
    - Opportunities
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
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
  target: app/Mcp/Tools/BaseShowTool.php
---

# View record — task mcp

## Trigger

The actor requests this task operation through mcp.

## Outcome

The selected record is returned under this transport’s disclosure contract. Allowed related collections return at most 25 newest items with returned/total/truncated metadata; unknown includes are ignored.
