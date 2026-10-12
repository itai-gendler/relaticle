---
kind: validation
routes:
  main: Unavailable model
steps:
- text: The selected model is unavailable under the current catalogue and plan or trial.
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

# Unavailable model

## Trigger

The selected model is unavailable under the current catalogue and plan or trial.

## Outcome

The request reports model unavailability rather than starting that model.
