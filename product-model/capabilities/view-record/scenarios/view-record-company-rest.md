---
kind: primary
routes:
  main: View record — company rest
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::company
  actor: workspace-viewer
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
    - Account Owner
    - Domains
    - ICP
    - LinkedIn
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: rest-api::company
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/CompaniesController.php
---

# View record — company rest

## Trigger

The actor requests this company operation through rest.

## Outcome

The selected record is returned under this transport’s disclosure contract. The controller loads configured values and does not process arbitrary selected-record includes.
