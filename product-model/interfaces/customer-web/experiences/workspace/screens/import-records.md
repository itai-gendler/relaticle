---
entities:
- entity: import
  shows:
  - File Name
  - Record Type
  - Column Mappings
  - Corrections
  - Matching Choices
  - Headers
  - Total Rows
  - Created Rows
  - Updated Rows
  - Skipped Rows
  - Failed Rows
  - Completed At
  collects:
  - File Name
  - Record Type
  - Column Mappings
  - Corrections
  - Matching Choices
- entity: failed-import-row
  shows:
  - Original Values
  - Error
  - Import
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Livewire/ImportWizard.php
---

# Import records

One file process through mapping, value review, preview/matching, execution and row results.
