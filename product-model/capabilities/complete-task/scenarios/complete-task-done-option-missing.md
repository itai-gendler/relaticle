---
kind: validation
routes:
  main: Done option missing
steps:
- text: The working scope assigned work Status definition has no option named Done.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/CompleteTask.php
---

# Done option missing

## Trigger

The workspace Task Status definition has no option named Done.

## Outcome

Completion reports the observed 422 refusal and leaves Status unchanged.
