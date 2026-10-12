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
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource.php
---

# Notes

The workspace collection of Notes. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
