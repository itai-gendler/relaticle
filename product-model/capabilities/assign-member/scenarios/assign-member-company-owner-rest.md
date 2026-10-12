---
kind: primary
routes:
  main: "Assign member \u2014 company-owner rest"
steps:
- text: Choose the identity assignment change
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::company
  actor: workspace-member
- text: The Product saves the assignment change
  kind: product
  entities:
  - entity: company
    effect: changes
    facts:
    - Account Owner
    - Changed At
  contexts:
    main:
      place: rest-api::company
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Company/UpdateCompany.php
---

# Assign member — company-owner rest

## Trigger

The actor supplies an assignment change.

## Outcome

The specified Account Owner assignment is retained.
