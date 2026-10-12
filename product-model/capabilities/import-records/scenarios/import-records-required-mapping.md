---
kind: validation
routes:
  main: Required mapping
steps:
- text: One or more required fields have no chosen mapping.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
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
---

# Required mapping

## Trigger

One or more required fields have no chosen mapping.

## Outcome

The process remains in mapping with the required-field problem.
