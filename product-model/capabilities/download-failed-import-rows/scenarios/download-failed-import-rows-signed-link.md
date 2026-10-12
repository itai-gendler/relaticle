---
kind: primary
routes:
  main: Download failed rows — signed-link
steps:
- text: Request the failed-row output
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-viewer
- text: The Product streams the retained original rows and errors
  kind: product
  entities:
  - entity: import
    effect: reads
    facts:
    - Headers
    - Failed Rows
  - entity: failed-import-row
    effect: reads
    facts:
    - Original Values
    - Error
    - Import
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Http/Controllers/DownloadFailedRowsController.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Livewire/Steps/PreviewStep.php
---

# Download failed rows — signed-link

## Trigger

Failed original rows exist for this import. The current workspace and the valid signed link match.

## Outcome

The output contains original input columns plus the retained error for each failed row, without changing records.
