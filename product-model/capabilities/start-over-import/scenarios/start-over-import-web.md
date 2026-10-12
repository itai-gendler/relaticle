---
kind: primary
routes:
  main: Start over the import
steps:
- text: Choose Start over
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product removes the unfinished import and resets the uploader
  kind: product
  entities:
  - entity: import
    effect: removes
    from: Mapping
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
  target: packages/ImportWizard/src/Livewire/Steps/MappingStep.php
---

# Start over the import

## Trigger

The offered Start over control is used while configuring an unfinished import.

## Outcome

The current workspace import/store is removed and the process returns to upload. No executing-import cancellation contract is inferred.
