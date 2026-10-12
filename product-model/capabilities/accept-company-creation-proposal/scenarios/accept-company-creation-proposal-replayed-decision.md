---
kind: validation
routes:
  main: Replayed decision does not write again
steps:
- text: The creation proposal already has a resolved decision.
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
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
---

# Replayed decision does not write again

## Trigger

The creation proposal already has a resolved decision.

## Outcome

The replay is refused and no duplicate Company is created.
