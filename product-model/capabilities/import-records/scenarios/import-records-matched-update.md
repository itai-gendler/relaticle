---
kind: primary
routes:
  main: Matched row changes existing record
steps:
- text: Confirm the matched-update preview
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product executes the matched row and records its update count
  kind: product
  entities:
  - entity: company
    effect: changes
    facts:
    - Name
    - Account Owner
    - Additional Values
    - Changed At
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
  target: packages/ImportWizard/src/Importers/BaseImporter.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Support/MatchResolver.php
---

# Matched row changes existing record

## Trigger

A Company row resolves an existing match under update behavior.

## Outcome

The existing record retains supplied filled native information and configured values; blank native inputs do not imply action-path clearing. No extra Company is created for that row.
