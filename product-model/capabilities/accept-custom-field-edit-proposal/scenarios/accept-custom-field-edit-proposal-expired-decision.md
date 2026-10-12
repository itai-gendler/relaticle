---
kind: edge
routes:
  main: Expired field decision
steps:
- text: The deadline has elapsed
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
- text: Choose Approve
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product closes the expired decision without a definition write
  kind: product
  entities:
  - entity: custom-field-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
---

# Expired field decision

## Trigger

A pending field edit has passed its retained validity deadline.

## Outcome

The proposal becomes Expired and the definition is unchanged.
