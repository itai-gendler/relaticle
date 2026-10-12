---
kind: primary
routes:
  main: View record — person rela
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product returns the requested CRM results and emits their display block unless lookup was requested
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
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/People.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseReadShowTool.php
---

# View record — person rela

## Trigger

The actor requests this person operation through rela.

## Outcome

The selected record is returned under this transport’s disclosure contract. Selected related collections contain at most ten newest items with true totals; unknown includes return an error. Note body remains directly available, while related free text is stripped and capped.
