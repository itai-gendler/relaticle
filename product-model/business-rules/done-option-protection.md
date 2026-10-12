---
appliesTo:
- type: entity
  id: custom-field-option
  effect: changes
  facts:
  - Name
- type: entity
  id: custom-field-option
  effect: removes
references:
- kind: code
  role: implementation
  target: app/Actions/CustomFields/SetCustomFieldOptions.php
---

# The existing Task Done option keeps its name and identity

A Task Status option plan cannot rename or remove the existing option named Done. Reordering is a distinct option-plan operation.
