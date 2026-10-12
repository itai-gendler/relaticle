---
kind: edge
routes:
  main: Mixed import rows retain failures
steps:
- text: Start the resolved preview
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product commits successful rows and retains failed rows independently
  kind: product
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Account Owner
    - Domains
    - ICP
    - LinkedIn
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  - entity: failed-import-row
    effect: creates
    facts:
    - Original Values
    - Error
    - Import
    to: Recorded
  - entity: import
    effect: changes
    facts:
    - Created Rows
    - Failed Rows
    - Completed At
    from: Importing
    to: Completed
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

# Mixed import rows retain failures

## Trigger

One validated row succeeds and another fails during execution.

## Outcome

The successful record remains; original values and the failed row’s error are retained, row counters show both outcomes and completed work is not rolled back.
