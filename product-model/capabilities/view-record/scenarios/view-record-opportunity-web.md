---
kind: primary
routes:
  main: View record — opportunity web
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
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
      place: customer-web::workspace::opportunity
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
---

# View record — opportunity web

## Trigger

The actor requests this opportunity operation through web.

## Outcome

The selected record is returned under this transport’s disclosure contract.
