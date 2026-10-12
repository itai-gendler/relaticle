---
kind: primary
routes:
  main: Opportunity deletion preserves linked work
steps:
- text: Confirm deletion
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
- text: The Product soft-deletes only the selected record
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Opportunity/DeleteOpportunity.php
---

# Opportunity deletion preserves linked work

## Trigger

An Opportunity has linked Tasks, Notes, Company and Point of Contact.

## Outcome

Only the Opportunity is soft-deleted; linked Tasks, Notes, Company and Person remain independent active records.
