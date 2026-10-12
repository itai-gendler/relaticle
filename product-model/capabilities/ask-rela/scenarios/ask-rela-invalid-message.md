---
kind: validation
routes:
  main: Invalid message
steps:
- text: The submitted submitted text is empty or exceeds 5,000 characters.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
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
  target: packages/Chat/src/Services/CreditService.php
---

# Invalid message

## Trigger

The submitted message is empty or exceeds 5,000 characters.

## Outcome

Validation reports the message error without starting generation.
