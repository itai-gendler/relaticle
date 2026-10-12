---
kind: edge
routes:
  main: Import store unavailable
steps:
- text: The file process store is unavailable
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
- text: Continue the current process
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product records the observed process failure
  kind: product
  entities:
  - entity: import
    effect: changes
    facts: []
    from: Importing
    to: Failed
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Livewire/ImportWizard.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Jobs/ExecuteImportJob.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Store/ImportStore.php
---

# Import store unavailable

## Trigger

The process cannot load its retained import store.

## Outcome

The observed process failure is reported rather than silently interpreting the missing store as an empty successful import. Earlier row outcomes are not reversed.
