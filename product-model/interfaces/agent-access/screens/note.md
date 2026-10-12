---
entities:
- entity: note
  shows:
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
  collects:
  - Title
  - Body
  - Companies
  - People
  - Opportunities
  - Additional Values
- entity: company
  shows:
  - Name
- entity: person
  shows:
  - Name
- entity: opportunity
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/NoteResource.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Note

One selected note with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
