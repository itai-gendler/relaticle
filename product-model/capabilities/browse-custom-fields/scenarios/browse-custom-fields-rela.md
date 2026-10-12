---
kind: primary
routes:
  main: "Discover fields \u2014 rela"
steps:
- text: Request the definition catalogue
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
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
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/CustomField/ListCustomFieldsTool.php
---

# Discover fields — rela

## Trigger

The actor requests workspace field definitions.

## Outcome

REST returns active definitions; this rela path returns its established definitions and option information. Inactive definitions can be returned on this path.
