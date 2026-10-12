---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Companies
  - People
  - Opportunities
  - Assignees
- type: entity
  id: note
  effect: changes
  facts:
  - Companies
  - People
  - Opportunities
references:
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
- kind: code
  role: implementation
  target: app/Actions/Note/UpdateNote.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Task/UpdateTaskTool.php
---

# Supplied lists replace while omitted lists remain

Task and Note updates check supplied collection-key presence. Omitted lists remain; supplied lists replace; empty arrays clear. Rela normalizes explicitly null Task lists to empty lists. REST null behavior is not generalized from that normalization.
