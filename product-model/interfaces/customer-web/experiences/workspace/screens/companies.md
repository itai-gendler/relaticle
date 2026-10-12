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
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/CompanyResource.php
---

# Companies

The workspace collection of Companies. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
