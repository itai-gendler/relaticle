---
appliesTo:
- type: entity
  id: custom-field
  effect: creates
- type: entity
  id: custom-field
  effect: changes
- type: entity
  id: custom-field
  effect: removes
references:
- kind: code
  role: implementation
  target: app/Support/CustomFieldDefinitionValidator.php
- kind: code
  role: implementation
  target: app/Actions/CustomFields/CreateCustomField.php
---

# Field definitions keep workspace limits and protections

The action supports its 17 declared types. Names are trimmed, required and at most 50 characters; case-insensitive name uniqueness and case-sensitive code uniqueness include inactive definitions within the workspace and record type. Explicit codes are at most 50 characters and alpha-dash; omitted codes generate uniquely. Choice fields require options; other types prohibit them. Limits default to 50 fields per record type and 50 options. System definitions keep names and cannot be deactivated; inactive ones may be reactivated. System deletion is refused; active definitions with values must be deactivated first.
