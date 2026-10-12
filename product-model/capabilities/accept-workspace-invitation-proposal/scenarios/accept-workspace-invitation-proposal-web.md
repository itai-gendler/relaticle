---
kind: primary
routes:
  main: Accept workspace invitation proposal
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
  - entity: workspace-invitation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    - Results
    from: Proposed
    to: Accepted
  - entity: workspace-invitation
    effect: creates
    facts:
    - Email
    - Role
    - Inviter
    - Workspace
    - Issued At
    - Expires At
    - Invitation Credential
    to: Issued
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

# Accept workspace invitation proposal

## Trigger

The requester selects the retained pending proposal’s decision.

## Outcome

The proposal becomes Accepted and its rechecked target operation is retained with actual results. Whole batches resolve per item; replaying a decision cannot write twice.
