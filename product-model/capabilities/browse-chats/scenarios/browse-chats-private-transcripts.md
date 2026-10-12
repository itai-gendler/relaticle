---
kind: validation
routes:
  main: "Another Account\u2019s transcript is private"
steps:
- text: The requested transcript belongs to another identity.
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
  target: packages/Chat/src/Queries/ConversationsQuery.php
---

# Another Account’s transcript is private

## Trigger

The requested conversation belongs to another Account.

## Outcome

No other Account’s transcript or proposals are disclosed.
