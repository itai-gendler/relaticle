---
kind: primary
routes:
  main: Unlink records — person-company rela
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
  - entity: person-edit-proposal
    effect: creates
    facts:
    - Targets
    - Earlier Person Values
    - Proposed Person Values
    - Proposed Company
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
  target: app/Actions/People/UpdatePeople.php
---

# Unlink records — person-company rela

## Trigger

The actor supplies a relationship change.

## Outcome

An edit proposal retains the desired Company changes without changing the target.
