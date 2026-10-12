---
kind: edge
routes:
  main: Rate limit
steps:
- text: The response meets the provider rate limit.
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

# Rate limit

## Trigger

The response meets the provider rate limit.

## Outcome

The inspected backoff/failure result is shown; failed generation follows credit resolution without reporting an unperformed write.
