---
kind: validation
routes:
  main: Credits exhausted
steps:
- text: The working scope cannot reserve the required credits.
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

# Credits exhausted

## Trigger

The workspace cannot reserve the required credits.

## Outcome

The request returns the observed 402 credit failure before generation.
