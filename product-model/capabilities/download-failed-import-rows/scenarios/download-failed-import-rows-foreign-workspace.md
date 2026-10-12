---
kind: validation
routes:
  main: Foreign import output refused
steps:
- text: "The signed request\u2019s file process working scope differs from the identity\u2019s current working scope."
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
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Http/Controllers/DownloadFailedRowsController.php
---

# Foreign import output refused

## Trigger

The signed request’s import workspace differs from the Account’s current workspace.

## Outcome

Delivery returns the observed 403 refusal without the foreign failed rows.
