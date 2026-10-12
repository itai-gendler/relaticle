---
entities:
- entity: person
  shows:
  - Name
  - Company
  - Emails
  - Phone Numbers
  - Job Title
  - LinkedIn
  - Additional Values
  - Creator
  - Creation Source
  - Created At
  - Changed At
  collects:
  - Name
  - Company
  - Emails
  - Phone Numbers
  - Job Title
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
  target: app/Http/Resources/V1/PeopleResource.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
---

# Person

One selected person with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
