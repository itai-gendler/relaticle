---
kind: validation
routes:
  main: Unresolved matches
steps:
- text: Preview still has unresolved matching decisions.
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

# Unresolved matches

## Trigger

Preview still has unresolved matching decisions.

## Outcome

Start does not enter execution until the required matching choices are resolved.
