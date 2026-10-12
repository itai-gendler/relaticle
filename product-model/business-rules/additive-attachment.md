---
appliesTo:
- type: capability
  id: link-records
- type: capability
  id: assign-member
- type: capability
  id: import-records
references:
- kind: code
  role: implementation
  target: app/Actions/Task/AttachTaskRelationships.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Support/EntityLinkStorage/MorphToManyStorage.php
---

# Dedicated attachment and import links preserve existing entries

Dedicated Task/Note attachment adds requested entries. Imported many-to-many links attach resolved targets without replacing existing links; an empty resolved list does not clear them.
