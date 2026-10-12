---
kind: primary
routes:
  main: Browse records — person web
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::people
  actor: workspace-viewer
- text: The Product returns the selected People collection using its native
    table controls
  kind: product
  entities:
  - entity: person
    effect: reads
    facts:
    - Name
    - Company
    - Emails
    - Phone Numbers
    - Job Title
    - LinkedIn
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::people
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/PeopleResource.php#table
- kind: code
  role: implementation
  target: app/Filament/Resources/PeopleResource/Pages/ListPeople.php
- kind: code
  role: implementation
  target: app/Filament/Concerns/HasCustomFieldColumns.php#table
---

# Browse records — person web

## Trigger

The actor requests this person operation through web.

## Outcome

The collection presents the native table’s record values and paging information. Its supported search and sort controls select results without changing records. Native filters cover creation source, deleted-record selection and the configured custom-field filters. These controls use the resource and custom-field table definitions; the REST/MCP/Rela filter-tree grammar is a separate contract.
