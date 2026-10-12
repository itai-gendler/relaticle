---
kind: primary
routes:
  main: Browse records — note web
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::notes
  actor: workspace-viewer
- text: The Product returns the selected Note collection using its native
    table controls
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
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::notes
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource.php#table
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource/Pages/ManageNotes.php
- kind: code
  role: implementation
  target: app/Filament/Concerns/HasCustomFieldColumns.php#table
---

# Browse records — note web

## Trigger

The actor requests this note operation through web.

## Outcome

The collection presents the native table’s record values and paging information. Its supported search and sort controls select results without changing records. Native filters cover creation source, deleted-record selection and the configured custom-field filters. These controls use the resource and custom-field table definitions; the REST/MCP/Rela filter-tree grammar is a separate contract.
