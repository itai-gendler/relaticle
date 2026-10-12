---
kind: validation
routes:
  main: Member permanent removal refused
steps:
- text: A Member requests permanent removal of a deleted record.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Policies/OpportunityPolicy.php
---

# Member permanent removal refused

## Trigger

A Member requests permanent removal of a deleted record.

## Outcome

The operation returns refusal and the deleted record remains retained.
