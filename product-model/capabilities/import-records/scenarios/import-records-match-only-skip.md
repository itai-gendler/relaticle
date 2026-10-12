---
kind: primary
routes:
  main: Unmatched match-only row is skipped
steps:
- text: Confirm match-only execution
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product records the unmatched row as skipped
  kind: product
  entities:
  - entity: import
    effect: changes
    facts:
    - Skipped Rows
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Support/MatchResolver.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Jobs/ExecuteImportJob.php
---

# Unmatched match-only row is skipped

## Trigger

A row has no existing match under match-only behavior.

## Outcome

The row is counted as skipped and creates no target record.
