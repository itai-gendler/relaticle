---
kind: primary
routes:
  main: "Browse records \u2014 opportunity mcp"
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunities
  actor: ai-agent
- text: The Product returns the working scope page with the declared filters, sort and stable pagination
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
      place: agent-access::opportunities
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: app/Queries/Opportunities/OpportunitiesQuery.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseListTool.php
---

# Browse records — opportunity mcp

## Trigger

The actor requests this opportunity operation through mcp.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records. To-many list expansion is refused; declared singular and count includes remain.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
- Company, Point of Contact and stale-days predicates use the declared Opportunity filters.
