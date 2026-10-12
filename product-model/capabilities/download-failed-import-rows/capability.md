---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Livewire/ImportWizard.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Jobs/ExecuteImportJob.php
---

# Download failed import rows

Obtain retained failed input rows and errors from the import process or a valid current-workspace signed link.
