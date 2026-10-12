---
entities:
- entity: custom-field
  shows:
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
  shows:
  - Name
  - Order
  - Field
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListCustomFieldsTool.php
---

# Custom fields

Definitions including inactive ones, with optional active filtering, and their options.
