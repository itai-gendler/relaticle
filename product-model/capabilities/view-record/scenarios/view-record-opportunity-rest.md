---
kind: primary
routes:
  main: View record — opportunity rest
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-viewer
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: opportunity
    effect: reads
    facts:
    - Name
    - Company
    - Point of Contact
    - Stage
    - Amount
    - Close Date
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/OpportunitiesController.php
---

# View record — opportunity rest

## Trigger

The actor requests this opportunity operation through rest.

## Outcome

The selected record is returned under this transport’s disclosure contract. The controller loads configured values and does not process arbitrary selected-record includes.
