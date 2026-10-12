---
kind: primary
routes:
  main: "Browse records \u2014 task rest"
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::tasks
  actor: workspace-viewer
- text: The Product returns the working scope page with the declared filters, sort and stable pagination
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
      place: rest-api::tasks
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
  target: app/Http/Controllers/Api/V1/TasksController.php
---

# Browse records — task rest

## Trigger

The actor requests this task operation through rest.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
- Assignee and assigned-to-me predicates remain distinct from linked CRM People.
