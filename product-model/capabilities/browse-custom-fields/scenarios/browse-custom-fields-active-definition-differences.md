---
kind: edge
routes:
  main: Inactive definition discovery differs
steps:
- text: Request inactive definitions
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::custom-fields
  actor: ai-agent
- text: The Product returns the MCP definition selection
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
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/CustomFieldsController.php
---

# Inactive definition discovery differs

## Trigger

The workspace has an inactive definition.

## Outcome

MCP can return it or apply its optional active filter. REST omits it. Rela definition discovery can return it, but ordinary writable custom-value schemas include active fields.
