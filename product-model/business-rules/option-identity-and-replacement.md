---
appliesTo:
- type: entity
  id: custom-field-option
  effect: creates
- type: entity
  id: custom-field-option
  effect: changes
- type: entity
  id: custom-field-option
  effect: removes
references:
- kind: code
  role: implementation
  target: app/Actions/CustomFields/SetCustomFieldOptions.php
- kind: code
  role: implementation
  target: app/Support/CustomFieldDefinitionValidator.php
---

# Rename preserves option identity and used removals need replacements

The full desired option list retains current identities on rename, orders the entries, adds new identities and supplies replacements for removed used entries. Replacement covers values on soft-deleted records too. Option names are nonempty, at most 255 characters and distinct ignoring case.
