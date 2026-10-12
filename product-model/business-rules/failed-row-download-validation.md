---
appliesTo:
- type: entity
  id: failed-import-row
  effect: reads
- type: entity
  id: import
  effect: reads
- type: capability
  id: download-failed-import-rows
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Http/Controllers/DownloadFailedRowsController.php
- kind: code
  role: implementation
  target: packages/ImportWizard/routes/web.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Livewire/Steps/PreviewStep.php
---

# Failed-row delivery requires signed current-Workspace matching

The download route requires authentication and signature, then the controller checks exact import/current-Account-workspace equality, returning 403 on mismatch. Output is original input columns plus Import Error. The process offers output only when complete with failures; the signed controller itself adds neither Data Import nor completion checks.
