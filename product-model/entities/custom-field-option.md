---
references:
- kind: code
  role: implementation
  target: app/Models/CustomFieldOption.php
---

# Custom Field Option

An addressable choice whose identity survives renaming and whose Order determines its position within its field.

## Information kept

- **Name** — The retained display name.
- **Order** — The retained position used by the applicable board or option ordering.
- **Field** — The retained field.

## States

### Present

The custom field option is present.
