---
kind: primary
routes:
  main: Create record — company rest
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::company
  actor: workspace-member
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: company
    effect: creates
    facts:
    - Name
    - Account Owner
    - Domains
    - ICP
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
      place: rest-api::company
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/CompaniesController.php
---

# Create record — company rest

## Trigger

The actor requests this company operation through rest.

## Outcome

A new active company is retained and returned. REST returns 201.
