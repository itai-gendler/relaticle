---
kind: primary
routes:
  main: Detach former member assignment
steps:
- text: Detach the existing former-member assignment
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product removes the requested assignment
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Assignees
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Task/DetachTaskRelationships.php
---

# Detach former member assignment

## Trigger

An existing Task Assignee no longer belongs to the workspace.

## Outcome

Dedicated detachment removes the stale assignment without a new-membership validation or assignment notification.
