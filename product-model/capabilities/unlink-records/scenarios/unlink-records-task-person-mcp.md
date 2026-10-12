---
kind: primary
routes:
  main: Unlink records — task-person mcp
steps:
- text: Choose the relationship entries to unlink
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - People
    - Changed At
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
---

# Unlink records — task-person mcp

## Trigger

The actor supplies a relationship change.

## Outcome

Specified entries are detached; other entries and linked records remain.
