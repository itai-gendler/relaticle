---
kind: primary
routes:
  main: "Delete record \u2014 task rela"
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the proposed operation for the requester’s decision
  kind: product
  entities:
  - entity: record-deletion-proposal
    effect: creates
    facts:
    - Record Kind
    - Targets
    - Requester
    - Workspace
    - Conversation
    - Turn
    - Valid Until
    - Decision
    - Decision Time
    - Dependencies
    - Results
    to: Proposed
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteDeleteTool.php
---

# Delete record — task rela

## Trigger

The actor requests this task operation through rela.

## Outcome

The record deletion proposal is retained and visible in Chat. The target remains unchanged until acceptance. Batch decisions operate per item.

## Edge cases

- Rela bounds the named targets to the workspace and skips missing or nondeletable entries. A proposal names one uniform record kind; no eligible targets returns the observed failure rather than a deletion. Accepted batches resolve per target, not by whole-batch approve.
