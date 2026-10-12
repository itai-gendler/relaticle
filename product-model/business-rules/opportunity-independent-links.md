---
appliesTo:
- type: entity
  id: opportunity
  effect: creates
  facts:
  - Company
  - Point of Contact
- type: entity
  id: opportunity
  effect: changes
  facts:
  - Company
  - Point of Contact
references:
- kind: code
  role: implementation
  target: app/Actions/Opportunity/CreateOpportunity.php
- kind: code
  role: implementation
  target: app/Actions/Opportunity/UpdateOpportunity.php
---

# Opportunity Company and Point of Contact remain independent

Both are optional workspace-owned links. The selected Person may belong to another Company in the same workspace. Changing or clearing either link preserves the other unless separately supplied.
