---
kind: primary
routes:
  main: Calendar date and datetime edits
steps:
- text: Supply the date and datetime changes
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-member
- text: The Product retains their distinct date and datetime semantics
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts:
    - Close Date
    - Additional Values
    - Changed At
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Filament/CustomFields/DateFieldType.php
- kind: code
  role: implementation
  target: app/Filament/CustomFields/DateTimeFieldType.php
---

# Calendar date and datetime edits

## Trigger

The actor edits Opportunity Close Date and configured datetime values.

## Outcome

Calendar dates retain the chosen date; datetime values use the traced timezone conversion. Due Date does not become a date-only value.
