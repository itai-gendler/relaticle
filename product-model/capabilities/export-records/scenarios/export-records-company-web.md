---
kind: primary
routes:
  main: Export records — company web
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
      place: customer-web::workspace::export-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
---

# Export records — company web

## Trigger

The actor requests this company operation through web.

## Outcome

The export is available; Due Date datetimes use the acting Account timezone and Close Date retains its calendar date.
