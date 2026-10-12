---
entities:
- entity: note
  shows:
  - Title
  - Body
  - Companies
  - People
  - Opportunities
  - Additional Values
  collects:
  - Title
  - Body
  - Companies
  - People
  - Opportunities
  - Additional Values
- entity: company
  shows:
  - Name
- entity: person
  shows:
  - Name
- entity: opportunity
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource.php
- kind: code
  role: implementation
  target: app/Filament/Resources/NoteResource/Forms/NoteForm.php#get
---

# Note

Current form values and linked selections for one selected Note.
