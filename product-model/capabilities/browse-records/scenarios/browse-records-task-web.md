---
kind: primary
routes:
  collection: Tasks collection
steps:
- text: Open the collection and choose search, filters, sorting or paging
  kind: actor
  entities: []
  contexts:
    collection:
      place: customer-web::workspace::tasks
  actor: workspace-viewer
- text: The Product returns the selected Task collection using its native
    table controls
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Status
    - Priority
    - Due Date
    - Description
    - Assignees
    - Companies
    - People
    - Opportunities
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    collection:
      place: customer-web::workspace::tasks
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource.php#table
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource/Pages/ManageTasks.php
- kind: code
  role: implementation
  target: app/Filament/Concerns/HasCustomFieldColumns.php#table
---

# Browse records — task web

## Trigger

The person opens the Tasks collection in the current workspace.

## Outcome

The collection presents the native table’s record values and paging information. Its supported search and sort controls select results without changing records. Native filters cover assigned-to-me, selected assignees, creation source, deleted-record selection and the configured custom-field filters; grouping uses Status or Priority when configured. These controls use the resource and custom-field table definitions; the REST/MCP/Rela filter-tree grammar is a separate contract.
