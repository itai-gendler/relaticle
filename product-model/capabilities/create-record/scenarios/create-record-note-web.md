---
kind: primary
routes:
  main: Create record — note web
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: note
    effect: creates
    facts:
    - Title
    - Body
    - Companies
    - People
    - Opportunities
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  contexts:
    main:
      place: customer-web::workspace::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
---

# Create record — note web

## Trigger

The actor requests this note operation through web.

## Outcome

A new active note is retained and returned.
