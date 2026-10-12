---
kind: primary
routes:
  main: Note rows create new Notes
steps:
- text: Confirm the resolved file preview
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
- text: The Product creates the new note row and records its count
  kind: product
  entities:
  - entity: note
    effect: creates
    facts:
    - Title
    - Body
    - Companies
    - People
    - Opportunities
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
  contexts:
    main:
      place: customer-web::workspace::import-records
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Importers/NoteImporter.php
---

# Note rows create new Notes

## Trigger

A Note input resembles an existing Note.

## Outcome

Execution creates a new Note rather than matching to update that Note; configured links remain additive.
