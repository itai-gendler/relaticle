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
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/NoteResource.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Notes

The workspace collection of Notes. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
