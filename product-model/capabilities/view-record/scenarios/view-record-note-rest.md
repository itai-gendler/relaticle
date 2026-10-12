---
kind: primary
routes:
  main: View record — note rest
steps:
- text: Select the record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::note
  actor: workspace-viewer
- text: The Product returns the selected record and the prescribed expansion
  kind: product
  entities:
  - entity: note
    effect: reads
    facts:
    - Title
    - Body
    - Companies
    - People
    - Opportunities
    - Additional Values
    - Creator
    - Creation Source
    - Created At
    - Changed At
  contexts:
    main:
      place: rest-api::note
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/NotesController.php
---

# View record — note rest

## Trigger

The actor requests this note operation through rest.

## Outcome

The selected record is returned under this transport’s disclosure contract. The controller loads configured values and does not process arbitrary selected-record includes.
