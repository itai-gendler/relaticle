---
kind: primary
routes:
  main: Rename personal Chat
steps:
- text: Supply the new title
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product retains the chosen title
  kind: product
  entities:
  - entity: conversation
    effect: changes
    facts:
    - Title
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Actions/RenameConversation.php
---

# Rename personal Chat

## Trigger

The Account supplies a new personal Chat title.

## Outcome

The chosen title is retained and reflected in the personal Chat list.
