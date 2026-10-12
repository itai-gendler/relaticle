---
kind: validation
routes:
  main: Foreign relationship target
steps:
- text: A requested linked record belongs to another working scope.
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

# Foreign relationship target

## Trigger

A requested linked record belongs to another workspace.

## Outcome

Reference validation fails; existing links remain.
