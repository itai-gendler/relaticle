---
kind: edge
routes:
  main: Execution progress is checkpointed
steps:
- text: Start the resolved preview
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product persists row progress and queues continuation
  kind: product
  entities:
  - entity: import
    effect: changes
    facts:
    - Created Rows
    - Updated Rows
    - Skipped Rows
    - Failed Rows
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Jobs/ExecuteImportJob.php
---

# Execution progress is checkpointed

## Trigger

Execution reaches its time box after some rows have committed.

## Outcome

Counters and progress checkpoints preserve committed rows; queued continuation resumes the inspected process rather than counting those rows again. This does not establish complete import-history recovery.
