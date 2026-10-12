---
kind: primary
routes:
  main: Unlink records — note-company mcp
steps:
- text: Choose the relationship entries to unlink
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
    - Companies
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

# Unlink records — note-company mcp

## Trigger

The actor supplies a relationship change.

## Outcome

Specified entries are detached; other entries and linked records remain.
