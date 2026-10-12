---
kind: primary
routes:
  main: View record — person rest
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::person
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
      place: rest-api::person
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/People.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/PeopleController.php
---

# View record — person rest

## Trigger

The actor requests this person operation through rest.

## Outcome

The selected record is returned under this transport’s disclosure contract. The controller loads configured values and does not process arbitrary selected-record includes.
