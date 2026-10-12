---
kind: primary
routes:
  main: Browse record history — mcp
steps:
- text: Request the change history
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product returns the scoped complete-save history
  kind: product
  entities:
  - entity: activity
    effect: reads
    facts:
    - Actor
    - Subject
    - Change
    - Source
    - Time
    - Import Summary
    - Workspace
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListActivityTool.php
---

# Browse record history — mcp

## Trigger

The actor requests one-record history.

## Outcome

The active visible selected record’s change history is returned. A soft-deleted or missing selected subject returns the traced not-found result; cross-record queries separately retain deleted-but-present subject activity. MCP pages at most 25 complete saves, default seven days and maximum 30, with continuation and total information.
