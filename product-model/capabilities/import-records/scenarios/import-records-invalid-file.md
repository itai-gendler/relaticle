---
kind: validation
routes:
  main: Invalid file
steps:
- text: The file is empty, oversized, over the configured row limit, not an accepted CSV/text file, or has duplicate
    headers.
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

# Invalid file

## Trigger

The file is empty, oversized, over the configured row limit, not an accepted CSV/text file, or has duplicate headers.

## Outcome

File validation reports the problem before mapping/execution; configured limits are 10 MB and 10,000 rows.
