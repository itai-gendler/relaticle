---
kind: primary
routes:
  main: "Edit record \u2014 note rela"
steps:
- text: "Supply changes to the record\u2019s own information"
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the proposed operation for the requester’s decision
  kind: product
  entities:
  - entity: note-edit-proposal
    effect: creates
    facts:
    - Targets
    - Earlier Note Values
    - Proposed Note Values
    - Proposed Companies
    - Proposed People
    - Proposed Opportunities
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
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteUpdateTool.php
---

# Edit record — note rela

## Trigger

The actor requests this note operation through rela.

## Outcome

The note edit proposal is retained and visible in Chat. The target remains unchanged until acceptance. Batch decisions operate per item.

## Edge cases

- Rela returns a whole-call error for a missing/foreign target, invalid name, configured value or reference. Entries with no supplied changes or unchanged values are omitted with reasons; an all-no-op request retains no proposal. Active field option labels are translated to option identities.
