---
kind: validation
routes:
  main: Foreign activity subject
steps:
- text: The requested subject is outside the working scope.
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
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
---

# Foreign activity subject

## Trigger

The requested subject is outside the workspace.

## Outcome

The request returns not found or refusal without foreign history.
