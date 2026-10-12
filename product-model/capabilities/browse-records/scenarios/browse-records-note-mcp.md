---
kind: primary
routes:
  main: "Browse records \u2014 note mcp"
steps:
- text: Choose the collection query, filter, sort or page
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::notes
  actor: ai-agent
- text: The Product returns the working scope page with the declared filters, sort and stable pagination
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
      place: agent-access::notes
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: app/Queries/Notes/NotesQuery.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseListTool.php
---

# Browse records — note mcp

## Trigger

The actor requests this note operation through mcp.

## Outcome

The workspace page and paging information are returned. Supported search, filter trees and sort select the result without changing records. To-many list expansion is refused; declared singular and count includes remain.

## Edge cases

- The shared filter tree supports AND, OR and NOT, native and configured values, and declared relation or member predicates. Default ordering is newest creation then identity for stable paging. Cursor paging permits native sort columns; configured-field sorting remains an offset-page path. Invalid fields, operators, depth, relation hops, lists or cursor shape return validation errors.
