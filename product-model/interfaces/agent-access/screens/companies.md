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
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/CompanyResource.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Companies

The workspace collection of Companies. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
