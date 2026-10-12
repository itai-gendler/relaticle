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
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/NoteResource.php
---

# Note

One selected note with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
