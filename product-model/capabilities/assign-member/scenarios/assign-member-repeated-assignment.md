---
kind: edge
routes:
  main: Repeated attachment does not renotify
steps:
- text: Attach the existing assignee again
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product retains the existing assignment without a new attachment
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
  target: app/Actions/Task/AttachTaskRelationships.php
- kind: code
  role: implementation
  target: app/Actions/Task/NotifyTaskAssignees.php
---

# Repeated attachment does not renotify

## Trigger

An already attached Task Assignee is supplied again through dedicated attachment.

## Outcome

The assignment remains once and no newly-attached-assignee notification is issued for it.
