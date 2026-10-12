---
appliesTo:
- type: entity
  id: failed-import-row
  effect: creates
  to: Recorded
permits:
- related:
  - verb: has failures
    entity: import
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: has failures
    entity: import
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: has failures
    entity: import
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  when:
  - entity: membership
    fact: Role
    is: Member
- unattended: true
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Jobs/ExecuteImportJob.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Http/Controllers/DownloadFailedRowsController.php
---

# The import process may retain failed original rows

A row execution failure records its original values/error in the same process; it does not undo successful row transactions.
