---
kind: primary
routes:
  main: Create record — note rest
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::note
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
      place: rest-api::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/NotesController.php
---

# Create record — note rest

## Trigger

The actor requests this note operation through rest.

## Outcome

A new active note is retained and returned. REST returns 201.
