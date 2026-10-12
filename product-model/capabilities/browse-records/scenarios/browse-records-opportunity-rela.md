---
kind: primary
routes:
  main: Browse records — opportunity rela
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
  - entity: opportunity
    effect: reads
    facts:
    - Name
    - Company
    - Point of Contact
    - Stage
    - Amount
    - Close Date
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
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: app/Queries/Opportunities/OpportunitiesQuery.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseReadListTool.php
---

# Browse records — opportunity rela

## Trigger

The actor requests this opportunity operation through rela.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records. Related list results contain at most three newest items per row with true totals.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
- Company, Point of Contact and stale-days predicates use the declared Opportunity filters.
