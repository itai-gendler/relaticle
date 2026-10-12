---
kind: primary
routes:
  main: View record — company web
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::company
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
      place: customer-web::workspace::company
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
---

# View record — company web

## Trigger

The actor requests this company operation through web.

## Outcome

The selected record is returned under this transport’s disclosure contract.
