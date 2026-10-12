---
kind: primary
routes:
  main: "Unassign member \u2014 company-owner rela"
steps:
- text: Choose the identity assignment change
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the edit proposal
  kind: product
  entities:
  - entity: company-edit-proposal
    effect: creates
    facts:
    - Targets
    - Earlier Company Values
    - Proposed Company Values
    - Proposed Account Owner
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
  target: app/Actions/Company/UpdateCompany.php
---

# Unassign member — company-owner rela

## Trigger

The actor supplies an assignment change.

## Outcome

The assignment change is retained in an edit proposal; the record remains unchanged.
