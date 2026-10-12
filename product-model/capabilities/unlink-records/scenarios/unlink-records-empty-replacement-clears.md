---
kind: primary
routes:
  main: Empty relationship replacement clears
steps:
- text: Supply an empty replacement list
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::note
  actor: workspace-member
- text: The Product clears only the supplied collection
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

# Empty relationship replacement clears

## Trigger

A Note edit explicitly supplies an empty Opportunities list.

## Outcome

The Note’s Opportunities collection becomes empty while omitted Companies and People remain.
