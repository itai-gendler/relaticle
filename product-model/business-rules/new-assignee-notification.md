---
appliesTo:
- type: entity
  id: task
  effect: creates
  facts:
  - Assignees
- type: entity
  id: task
  effect: changes
  facts:
  - Assignees
references:
- kind: code
  role: implementation
  target: app/Actions/Task/NotifyTaskAssignees.php
- kind: code
  role: implementation
  target: app/Actions/Task/CreateTask.php
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
- kind: code
  role: implementation
  target: app/Filament/Actions/CreateTaskAction.php#callAfter
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource.php#table
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource/Forms/TaskForm.php#get
- kind: code
  role: implementation
  target: app/Actions/Task/AttachTaskRelationships.php#execute
---

# Task assignment notifications follow the explicit action and creation hooks

CreateTask, UpdateTask and dedicated attachment collect newly attached assignee_ids and invoke notification handling after their transaction, according to in-app and email preferences. Repeated attachment does not notify again. Native CreateTaskAction captures the submitted assignees before creation and invokes the same notification handler afterward on the collection, Home and board creation paths.

The native table’s own-attribute handler calls UpdateTask, but its relationship form uses assignees rather than assignee_ids. This does not establish uniform relationship-edit notification parity. Board card edits and direct importer writes have no equivalent explicit notification hook in the inspected code. Native relationship persistence remains dependency-owned.
