---
kind: primary
routes:
  main: Export records — person web
steps:
- text: Select record information to export
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::export-records
  actor: workspace-member
- text: The Product generates the selected export
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
      place: customer-web::workspace::export-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/People.php
---

# Export records — person web

## Trigger

The actor requests this person operation through web.

## Outcome

The export is available; Due Date datetimes use the acting Account timezone and Close Date retains its calendar date.
