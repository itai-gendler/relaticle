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
- entity: task
  shows:
  - Title
- entity: note
  shows:
  - Title
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/OpportunityResource.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Opportunity

One selected opportunity with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
