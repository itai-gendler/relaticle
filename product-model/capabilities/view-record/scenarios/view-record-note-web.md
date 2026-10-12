---
kind: primary
routes:
  main: View record — note web
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
- text: The Product shows the selected Note form values and linked selections
  kind: product
  entities:
  - entity: note
    effect: reads
    facts:
    - Title
    - Body
    - Companies
    - People
    - Opportunities
    - Additional Values
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource.php
- kind: code
  role: implementation
  target: app/Policies/NotePolicy.php#update
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource/Forms/NoteForm.php#get
---

# View record — note web

## Trigger

The person opens the selected Note through its native edit control.

## Outcome

The selected Note editor presents its own form values and linked selections without changing the record. Collection, REST, MCP and Rela reads retain their separate disclosure contracts.
