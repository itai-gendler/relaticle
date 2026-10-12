---
kind: edge
routes:
  main: Dismiss pending dependent steps
steps:
- text: Reject the earlier proposal
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product closes the selected proposal and pending dependent step
  kind: product
  entities:
  - entity: company-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Dismissed
  - entity: person-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    - Results
    from: Proposed
    to: Dismissed
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
---

# Dismiss pending dependent steps

## Trigger

Pending Person creation depends on a pending Company creation that the requester rejects.

## Outcome

The selected and pending dependent proposals become Dismissed with the dependency reason. Earlier accepted steps and their records remain.
