---
references:
- kind: code
  role: implementation
  target: app/Models/CustomField.php
relations:
- entity: custom-field-option
  verb: has options
  cardinality: one-to-many
---

# Custom Field

An addressable workspace definition of a configured record value. This scope describes its common definition facts.

## Information kept

- **Name** — The retained display name.
- **Code** — The retained code.
- **Record Type** — The retained record type.
- **Field Type** — The retained field type.
- **Active** — The retained active.
- **System Defined** — The retained system defined.
- **Required** — The retained required.
- **Order** — The retained position used by the applicable board or option ordering.
- **Workspace** — The workspace to which this instance belongs.

## States

### Present

The custom field is present.
