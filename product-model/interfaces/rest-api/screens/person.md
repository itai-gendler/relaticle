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
references:
- kind: code
  role: implementation
  target: app/Http/Resources/V1/PeopleResource.php
---

# Person

One selected person with the facts published by this transport. Related expansion is bounded and allowed only as this contract establishes.
