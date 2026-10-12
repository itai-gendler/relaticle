---
kind: validation
routes:
  main: Invalid new assignee
steps:
- text: A supplied new assignee is not a member of the resolved working scope.
  kind: condition
  entities: []
  contexts:
    main:
      place: rest-api::task
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
---

# Invalid new assignee

## Trigger

A supplied new assignee is not a member of the resolved workspace.

## Outcome

The update fails validation and the Task information and assignments remain unchanged.
