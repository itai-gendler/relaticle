---
kind: primary
routes:
  main: Accept custom field edit proposal
steps:
- text: Choose Approve for the retained proposal
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product resolves approved dependencies, executes the target operation and retains the result
  kind: product
  entities:
  - entity: custom-field-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    - Results
    from: Proposed
    to: Accepted
  - entity: custom-field
    effect: changes
    facts:
    - Name
    - Active
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

# Accept custom field edit proposal

## Trigger

The requester selects the retained pending proposal’s decision.

## Outcome

The proposal becomes Accepted and its rechecked target operation is retained with actual results. Whole batches resolve per item; replaying a decision cannot write twice.
