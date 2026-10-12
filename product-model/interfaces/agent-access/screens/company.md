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
- entity: task
  shows:
  - Title
- entity: note
  shows:
  - Title
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/CompanyResource.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Company

One selected company with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
