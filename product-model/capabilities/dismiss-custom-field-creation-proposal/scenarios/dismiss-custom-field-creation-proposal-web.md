---
kind: primary
routes:
  main: Dismiss custom field creation proposal
steps:
- text: Choose Reject for the retained proposal
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product retains the dismissal decision
  kind: product
  entities:
  - entity: custom-field-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Dismissed
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
---

# Dismiss custom field creation proposal

## Trigger

The requester selects the retained pending proposal’s decision.

## Outcome

The proposal becomes Dismissed without a target write or reversal of earlier accepted work. Whole batches resolve per item; replaying a decision cannot write twice.
