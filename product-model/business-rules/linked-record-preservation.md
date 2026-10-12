---
appliesTo:
- type: entity
  id: company
  effect: changes
  to: Deleted
- type: entity
  id: person
  effect: changes
  to: Deleted
- type: entity
  id: opportunity
  effect: changes
  to: Deleted
- type: entity
  id: task
  effect: changes
  to: Deleted
- type: entity
  id: note
  effect: changes
  to: Deleted
- type: entity
  id: company
  effect: removes
- type: entity
  id: person
  effect: removes
- type: entity
  id: opportunity
  effect: removes
- type: entity
  id: task
  effect: removes
- type: entity
  id: note
  effect: removes
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: app/Actions/Task/DeleteTask.php
---

# Deleting one CRM record preserves independent linked records

Soft deletion and permanent removal do not delete independent Companies, People, Opportunities, Tasks or Notes linked to the selected record. Association cleanup does not imply cascading record deletion.
