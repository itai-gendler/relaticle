---
entities:
- entity: company
  shows:
  - Name
  - Account Owner
  - Domains
  - ICP
  - LinkedIn
  - Additional Values
  - Creator
  - Creation Source
  - Created At
  - Changed At
  collects:
  - Name
  - Account Owner
  - Domains
  - ICP
  - LinkedIn
  - Additional Values
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/CompanyResource.php
---

# Company

One selected company with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
