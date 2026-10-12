---
kind: primary
routes:
  main: Link records — note-person mcp
steps:
- text: Choose the relationship entries to link
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::note
  actor: ai-agent
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: note
    effect: changes
    facts:
    - People
    - Changed At
  contexts:
    main:
      place: agent-access::note
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Note/UpdateNote.php
---

# Link records — note-person mcp

## Trigger

The actor supplies a relationship change.

## Outcome

The requested entries are linked; dedicated attachment retains existing entries while supplied edit collections replace them.
