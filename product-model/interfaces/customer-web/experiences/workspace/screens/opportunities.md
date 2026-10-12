---
entities:
- entity: opportunity
  shows:
  - Name
  - Company
  - Point of Contact
  - Stage
  - Amount
  - Close Date
  - Additional Values
  - Order
  collects:
  - Order
  - Stage
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/OpportunityResource.php
---

# Opportunities

The workspace collection of Opportunities. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
