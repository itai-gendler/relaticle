---
kind: primary
routes:
  main: Import adds Task links
steps:
- text: Confirm the assigned work link preview
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product stores additive resolved links and row progress
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Companies
    - People
    - Opportunities
  - entity: import
    effect: changes
    facts:
    - Updated Rows
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Support/EntityLinkStorage/MorphToManyStorage.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Importers/TaskImporter.php
---

# Import adds Task links

## Trigger

A matched Task already has an Opportunity link and imported links resolve additional records.

## Outcome

Resolved links are added without removing existing links; an empty resolved list does not clear them. Task-assignee notifications are not promised for direct importer writes.
