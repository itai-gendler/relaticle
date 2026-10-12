---
kind: primary
routes:
  main: "Create record \u2014 opportunity rela"
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the proposed operation for the requester’s decision
  kind: product
  entities:
  - entity: opportunity-creation-proposal
    effect: creates
    facts:
    - Proposed Name
    - Proposed Company
    - Proposed Point of Contact
    - Proposed Additional Values
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
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteCreateTool.php
---

# Create record — opportunity rela

## Trigger

The actor requests this opportunity operation through rela.

## Outcome

The opportunity creation proposal is retained and visible in Chat. The target remains unchanged until acceptance. Batch decisions operate per item.

## Edge cases

- Rela requires a nonempty batch and enforces the configured default-25 limit and plan-step cap. Invalid names, configured values or foreign references skip their individual creation entries with reasons; valid entries remain in one proposal. Nonobject entries fail the call; if every entry fails, no proposal is retained.
