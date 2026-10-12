---
kind: primary
routes:
  main: "Browse records \u2014 person rest"
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::people
  actor: workspace-viewer
- text: The Product returns the working scope page with the declared filters, sort and stable pagination
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
      place: rest-api::people
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/People.php
- kind: code
  role: implementation
  target: app/Queries/People/PeopleQuery.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/PeopleController.php
---

# Browse records — person rest

## Trigger

The actor requests this person operation through rest.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
