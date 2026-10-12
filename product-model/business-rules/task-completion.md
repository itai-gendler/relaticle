---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Status
- type: capability
  id: complete-task
references:
- kind: code
  role: implementation
  target: app/Actions/Task/CompleteTask.php
---

# Completion selects the Workspace option named Done

CompleteTask resolves the Task Status definition in the record workspace and its option named exactly Done. If it is absent the observed 422 refusal leaves Status unchanged. The prior custom-field tenant is restored.
