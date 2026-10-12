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
  - Creator
  - Creation Source
  - Created At
  - Changed At
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/OpportunityResource.php
---

# Opportunities

The workspace collection of Opportunities. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
