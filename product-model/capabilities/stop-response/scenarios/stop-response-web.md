---
kind: primary
routes:
  main: Stop the response
steps:
- text: Choose Stop
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product records the cancellation signal and stops the visible stream
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Http/Controllers/ChatController.php
- kind: code
  role: implementation
  target: packages/Chat/src/Jobs/ProcessChatMessage.php
---

# Stop the response

## Trigger

A personal response is streaming.

## Outcome

Visible streaming stops after the stop signal. Provider generation may continue until its inspected completion check and credit settlement; this does not undo accepted CRM work.
