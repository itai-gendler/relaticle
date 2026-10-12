---
appliesTo:
- type: entity
  id: import
  effect: reads
permits:
- related:
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
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
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when:
  - entity: membership
    fact: Role
    is: Viewer
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

# Current workspace members may read the offered import output

The offered process uses Data Import. Signed failed-row delivery instead requires valid signature, authenticated request and exact current-workspace equality, without a Data Import check. The narrower output does not grant general import-history access.
