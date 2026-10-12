---
kind: primary
routes:
  main: Accept company creation proposal
steps:
- text: Choose Approve for the retained proposal
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product resolves approved dependencies, executes the target operation and retains the result
  kind: product
  entities:
  - entity: company-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    - Results
    from: Proposed
    to: Accepted
  - entity: company
    effect: creates
    facts:
    - Name
    - Account Owner
    - Domains
    - ICP
    - LinkedIn
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
---

# Accept company creation proposal

## Trigger

The requester selects the retained pending proposal’s decision.

## Outcome

The proposal becomes Accepted and its rechecked target operation is retained with actual results. Whole batches resolve per item; replaying a decision cannot write twice.
