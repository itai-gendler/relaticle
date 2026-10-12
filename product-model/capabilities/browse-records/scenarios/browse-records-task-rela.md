---
kind: primary
routes:
  main: Browse records — task rela
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product returns the requested CRM results and emits their display block unless lookup was requested
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
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
- kind: code
  role: implementation
  target: app/Queries/Tasks/TasksQuery.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseReadListTool.php
---

# Browse records — task rela

## Trigger

The actor requests this task operation through rela.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records. Related list results contain at most three newest items per row with true totals.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
- Assignee and assigned-to-me predicates remain distinct from linked CRM People.
