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
  collects:
  - Name
  - Company
  - Point of Contact
  - Stage
  - Amount
  - Close Date
  - Additional Values
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/OpportunityResource.php
---

# Opportunity

One selected opportunity with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
