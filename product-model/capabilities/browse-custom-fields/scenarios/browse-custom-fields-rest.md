---
kind: primary
routes:
  main: "Discover fields \u2014 rest"
steps:
- text: Request the definition catalogue
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::custom-fields
  actor: workspace-viewer
- text: The Product returns the working scope definition catalogue
  kind: product
  entities:
  - entity: custom-field
    effect: reads
    facts:
    - Name
    - Code
    - Record Type
    - Field Type
    - Active
    - System Defined
    - Required
    - Order
    - Workspace
  - entity: custom-field-option
    effect: reads
    facts:
    - Name
    - Order
    - Field
  contexts:
    main:
      place: rest-api::custom-fields
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/CustomFieldsController.php
---

# Discover fields — rest

## Trigger

The actor requests workspace field definitions.

## Outcome

REST returns active definitions; this rest path returns its established definitions and option information.
