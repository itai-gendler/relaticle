---
appliesTo:
- type: entity
  id: task
  facts:
  - Due Date
- type: entity
  id: opportunity
  facts:
  - Close Date
references:
- kind: code
  role: implementation
  target: app/Filament/Exports/BaseExporter.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Rules/ImportDateRule.php
- kind: code
  role: implementation
  target: app/Filament/CustomFields/DateTimeFieldType.php
- kind: code
  role: implementation
  target: app/Filament/CustomFields/DateFieldType.php
---

# Datetimes use applicable timezone and dates retain their date

Task Due Date is a UTC datetime. Traced datetime-column, Rela and export presentation applies the applicable Account timezone. Opportunity Close Date is a calendar date. Export uses the exporting Account timezone; import parses using the original Account timezone. Date-only values do not shift like datetimes.

The REST/MCP shared resource formatter returns the underlying nonchoice values without a viewer-timezone conversion of its own. Rela’s LocalisesDatetimes and native display/export paths apply their traced timezone presentation; this does not assert transport-wide presentation parity.

Home formats the date of its parsed due timestamp and separately derives severity from both Account-local midnight boundaries. That preview does not establish the full collection’s timezone display or fact disclosure.
