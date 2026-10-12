---
kind: validation
routes:
  main: Foreign assignment
steps:
- text: The requested new identity is outside the current working scope.
  kind: condition
  entities: []
  contexts:
    main:
      place: agent-access::task
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Task/AttachTaskRelationships.php
---

# Foreign assignment

## Trigger

The requested new Account is outside the current workspace.

## Outcome

Assignment validation fails without attaching the Account or issuing a new-assignee notification.
