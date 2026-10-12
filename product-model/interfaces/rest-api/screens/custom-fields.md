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
  target: app/Http/Controllers/Api/V1/CustomFieldsController.php
---

# Custom fields

Active definitions and their options.
