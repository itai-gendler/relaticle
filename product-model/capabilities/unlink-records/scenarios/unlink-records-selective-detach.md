---
kind: primary
routes:
  main: Dedicated detachment is selective
steps:
- text: Detach the selected link
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product removes the specified link
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Opportunities
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Task/DetachTaskRelationships.php
---

# Dedicated detachment is selective

## Trigger

A Task links several Opportunities and one is requested for detachment.

## Outcome

Only the specified relationship is detached; other links and linked records remain.
