---
kind: validation
routes:
  main: Missing record name
steps:
- text: The new record’s required name is empty or invalid.
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
  target: app/Http/Requests/Api/V1/StoreOpportunityRequest.php
---

# Missing record name

## Trigger

The new record’s required name is empty or invalid.

## Outcome

Validation reports the required-name problem and no record is retained.
