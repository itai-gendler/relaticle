---
kind: validation
routes:
  main: Foreign Chat rename refused
steps:
- text: The selected transcript belongs to another identity or working scope.
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
  target: packages/Chat/src/Actions/RenameConversation.php
---

# Foreign Chat rename refused

## Trigger

The selected conversation belongs to another Account or workspace.

## Outcome

The rename is refused and its title remains.
