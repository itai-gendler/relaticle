---
kind: edge
routes:
  main: Earlier plan success survives later failure
steps:
- text: Approve the plan
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the successful earlier step and reports the later failure
  kind: product
  entities:
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
  - entity: company-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    - Results
    from: Proposed
    to: Accepted
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
---

# Earlier plan success survives later failure

## Trigger

A linked proposal plan fails after creating its Company.

## Outcome

The Company and its accepted result remain; the later failed step is reported without rolling back earlier accepted work.
