---
kind: primary
routes:
  main: Browse workspace activity — mcp
steps:
- text: Request the change history
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::workspace-activity
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
      place: agent-access::workspace-activity
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListActivityTool.php
---

# Browse workspace activity — mcp

## Trigger

The actor requests cross-record history.

## Outcome

The workspace activity page includes actor, subject, field changes, source, time and import summaries. MCP pages at most 25 complete saves, default seven days and maximum 30, with continuation and total information.
