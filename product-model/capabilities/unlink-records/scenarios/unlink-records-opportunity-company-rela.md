---
kind: primary
routes:
  main: Unlink records — opportunity-company rela
steps:
- text: Choose the relationship entries to unlink
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

# Unlink records — opportunity-company rela

## Trigger

The actor supplies a relationship change.

## Outcome

An edit proposal retains the desired Company changes without changing the target. Company and Point of Contact are independent and need not refer to matching Companies; clearing one preserves the other.
