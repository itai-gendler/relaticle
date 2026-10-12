---
kind: primary
routes:
  main: "Unassign member \u2014 task-assignee mcp"
steps:
- text: Choose the identity assignment change
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product saves the assignment change
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Assignees
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

# Unassign member — task-assignee mcp

## Trigger

The actor supplies an assignment change.

## Outcome

The specified Assignees assignment is removed without deleting the Account.
