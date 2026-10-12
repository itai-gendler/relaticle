---
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Models/Import.php
relations:
- entity: failed-import-row
  verb: has failures
  cardinality: one-to-many
---

# Import

One workspace import process, its mapping and correction choices, execution progress and observable row outcomes.

## Information kept

- **File Name** — The retained file name.
- **Record Type** — The retained record type.
- **Headers** — The retained headers.
- **Column Mappings** — The retained column mappings.
- **Corrections** — The retained corrections.
- **Matching Choices** — The retained matching choices.
- **Total Rows** — The retained total rows.
- **Created Rows** — The retained created rows.
- **Updated Rows** — The retained updated rows.
- **Skipped Rows** — The retained skipped rows.
- **Failed Rows** — The retained failed rows.
- **Completed At** — The retained completed at.
- **User** — The retained user.
- **Workspace** — The workspace to which this instance belongs.

## States

### Uploading

The import is uploading.

### Mapping

The import is mapping.

### Reviewing

The import is reviewing.

### Previewing

The import is previewing.

### Importing

The import is importing.

### Completed

Execution results and completion time are available.

### Failed

The import process has failed; prior completed rows can remain.
