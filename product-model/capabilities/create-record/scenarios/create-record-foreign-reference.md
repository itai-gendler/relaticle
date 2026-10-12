---
kind: validation
routes:
  main: Foreign creation reference
steps:
- text: A supplied link points outside the resolved working scope
  kind: condition
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Opportunity/CreateOpportunity.php
---

# Foreign creation reference

## Trigger

The proposed Company or Point of Contact belongs to another workspace.

## Outcome

The request fails reference validation and retains no Opportunity.
