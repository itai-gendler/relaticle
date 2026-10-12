---
kind: primary
routes:
  main: "Browse records \u2014 company rest"
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::companies
  actor: workspace-viewer
- text: The Product returns the working scope page with the declared filters, sort and stable pagination
  kind: product
  entities:
  - entity: company
    effect: reads
    facts:
    - Name
    - Account Owner
    - Domains
    - ICP
    - LinkedIn
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: rest-api::companies
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
- kind: code
  role: implementation
  target: app/Queries/Companies/CompaniesQuery.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/CompaniesController.php
---

# Browse records — company rest

## Trigger

The actor requests this company operation through rest.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
