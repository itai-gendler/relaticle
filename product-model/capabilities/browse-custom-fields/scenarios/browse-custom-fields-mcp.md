---
kind: primary
routes:
  main: "Discover fields \u2014 mcp"
steps:
- text: Request the definition catalogue
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::custom-fields
  actor: ai-agent
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
      place: agent-access::custom-fields
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListCustomFieldsTool.php
---

# Discover fields — mcp

## Trigger

The actor requests workspace field definitions.

## Outcome

REST returns active definitions; this mcp path returns its established definitions and option information. Inactive definitions can be returned on this path.
