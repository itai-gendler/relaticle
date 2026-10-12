---
kind: primary
routes:
  main: Export datetime presentation
steps:
- text: Request the selected export
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::export-records
  actor: workspace-member
- text: The Product formats the export using the applicable timezone
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due Date
    - Additional Values
  - entity: account
    effect: reads
    facts:
    - Timezone
  contexts:
    main:
      place: customer-web::workspace::export-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Filament/Exports/BaseExporter.php
---

# Export datetime presentation

## Trigger

A Task export is requested by an Account with a configured timezone.

## Outcome

The generated Task Due Date is presented in that Account’s timezone; date-only values retain their dates.
