---
kind: primary
routes:
  main: View record — person web
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-viewer
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: person
    effect: reads
    facts:
    - Name
    - Company
    - Emails
    - Phone Numbers
    - Job Title
    - LinkedIn
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/People.php
---

# View record — person web

## Trigger

The actor requests this person operation through web.

## Outcome

The selected record is returned under this transport’s disclosure contract.
