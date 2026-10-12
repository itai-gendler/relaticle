---
kind: primary
routes:
  main: Import opportunity records
steps:
- text: Supply the CSV file and record type
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product retains the parsed import file and headers
  kind: product
  entities:
  - entity: import
    effect: creates
    facts:
    - File Name
    - Record Type
    - Headers
    - Column Mappings
    - Corrections
    - Matching Choices
    - Total Rows
    - Created Rows
    - Updated Rows
    - Skipped Rows
    - Failed Rows
    - Completed At
    - User
    - Workspace
    to: Uploading
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product opens mapping after file parsing
  kind: product
  entities:
  - entity: import
    effect: changes
    facts:
    - Headers
    from: Uploading
    to: Mapping
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: Choose required field mappings
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product stores mappings and opens value review
  kind: product
  entities:
  - entity: import
    effect: changes
    facts:
    - Column Mappings
    from: Mapping
    to: Reviewing
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: Correct matching raw values in a column and choose matching behavior
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product stores corrections and matching choices and opens preview
  kind: product
  entities:
  - entity: import
    effect: changes
    facts:
    - Corrections
    - Matching Choices
    from: Reviewing
    to: Previewing
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: Confirm the resolved preview
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product locks the start and records execution progress
  kind: product
  entities:
  - entity: import
    effect: changes
    facts: []
    from: Previewing
    to: Importing
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product executes validated rows in the original working scope and creator context
  kind: product
  entities:
  - entity: opportunity
    effect: creates
    facts:
    - Name
    - Company
    - Point of Contact
    - Stage
    - Amount
    - Close Date
    - Order
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  - entity: import
    effect: changes
    facts:
    - Created Rows
    - Updated Rows
    - Skipped Rows
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
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Importers/OpportunityImporter.php
---

# Import opportunity records

## Trigger

The actor starts a file process for opportunity records.

## Outcome

The import completes with created, updated, skipped and failed row counts. Opportunity matching uses IDs; Company and Point of Contact remain independently resolved links. Execution is queued with the original Account/workspace and does not invent a later per-record role recheck. Individual row failures preserve other committed rows.
