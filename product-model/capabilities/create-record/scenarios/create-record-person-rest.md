---
kind: primary
routes:
  main: Create record — person rest
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::person
  actor: workspace-member
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: person
    effect: creates
    facts:
    - Name
    - Company
    - Emails
    - Phone Numbers
    - Job Title
    - LinkedIn
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  contexts:
    main:
      place: rest-api::person
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/People.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/PeopleController.php
---

# Create record — person rest

## Trigger

The actor requests this person operation through rest.

## Outcome

A new active person is retained and returned. REST returns 201.
