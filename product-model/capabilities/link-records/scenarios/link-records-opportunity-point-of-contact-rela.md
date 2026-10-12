---
kind: primary
routes:
  main: Link records — opportunity-point-of-contact rela
steps:
- text: Choose the relationship entries to link
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the edit proposal
  kind: product
  entities:
  - entity: opportunity-edit-proposal
    effect: creates
    facts:
    - Targets
    - Earlier Opportunity Values
    - Proposed Opportunity Values
    - Proposed Company
    - Proposed Point of Contact
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
  target: app/Actions/Opportunity/UpdateOpportunity.php
---

# Link records — opportunity-point-of-contact rela

## Trigger

The actor supplies a relationship change.

## Outcome

An edit proposal retains the desired Point of Contact changes without changing the target. Company and Point of Contact are independent and need not refer to matching Companies; clearing one preserves the other.
