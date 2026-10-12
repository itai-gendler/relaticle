---
kind: primary
routes:
  main: Unlink records — note-opportunity rest
steps:
- text: Choose the relationship entries to unlink
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::note
  actor: workspace-member
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: note
    effect: changes
    facts:
    - Opportunities
    - Changed At
  contexts:
    main:
      place: rest-api::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Note/UpdateNote.php
---

# Unlink records — note-opportunity rest

## Trigger

The actor supplies a relationship change.

## Outcome

Specified entries are detached; other entries and linked records remain.
