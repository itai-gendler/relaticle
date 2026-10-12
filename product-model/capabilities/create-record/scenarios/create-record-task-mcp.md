---
kind: primary
routes:
  main: Create record — task mcp
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: task
    effect: creates
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
    - Order
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
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
  target: app/Mcp/Tools/BaseCreateTool.php
---

# Create record — task mcp

## Trigger

The actor requests this task operation through mcp.

## Outcome

A new active task is retained and returned.
