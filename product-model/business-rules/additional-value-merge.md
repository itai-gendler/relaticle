---
appliesTo:
- type: entity
  id: company
  effect: changes
  facts:
  - Additional Values
- type: entity
  id: person
  effect: changes
  facts:
  - Additional Values
- type: entity
  id: opportunity
  effect: changes
  facts:
  - Additional Values
- type: entity
  id: task
  effect: changes
  facts:
  - Additional Values
- type: entity
  id: note
  effect: changes
  facts:
  - Additional Values
references:
- kind: code
  role: implementation
  target: app/Support/CustomFieldMerger.php
---

# Omitted configured values remain on traced updates

CustomFieldMerger preserves omitted existing configured values on action updates. This does not infer native-form, importer or transport-null parity.
