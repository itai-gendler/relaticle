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
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/PeopleResource.php
---

# People

The workspace collection of People. Filtering, sorting and paging retain the inspected transport’s grammar; board changes remain this collection context.
