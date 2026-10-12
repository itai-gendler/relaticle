---
kind: primary
routes:
  main: Link records — person-company mcp
steps:
- text: Choose the relationship entries to link
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: person
    effect: changes
    facts:
    - Company
    - Changed At
  contexts:
    main:
      place: agent-access::person
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/People/UpdatePeople.php
---

# Link records — person-company mcp

## Trigger

The actor supplies a relationship change.

## Outcome

The chosen Company link is retained.
