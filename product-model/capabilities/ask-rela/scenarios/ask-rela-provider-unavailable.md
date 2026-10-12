---
kind: edge
routes:
  main: Provider unavailable
steps:
- text: The outbound provider fails during generation.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
- text: Send the typed request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product retains the owned message and records the observed response failure with credit resolution
  kind: product
  entities:
  - entity: message
    effect: creates
    facts:
    - Content
    - Author
    - Conversation
    - Created At
    - Processing Outcome
    to: Present
  - entity: credit-balance
    effect: changes
    facts:
    - Remaining
    - Used
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Jobs/ProcessChatMessage.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/CreditService.php
---

# Provider unavailable

## Trigger

The outbound provider fails during generation.

## Outcome

The response reports failure, the retained typed message remains, unresolved proposals are closed by the inspected failure path, and reserved credits follow idempotent refund; accepted CRM work is preserved.
