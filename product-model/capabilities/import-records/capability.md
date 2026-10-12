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

# Import records

Import a file through mapping, value review, preview/matching, row execution and results. Matching creates, updates or skips; failed rows do not reverse completed rows.
