---
appliesTo:
- type: entity
  id: failed-import-row
  effect: reads
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

# Current workspace members may read offered failed rows

Data Import guards process output; signed delivery uses signature, authentication and exact current-workspace equality without a Data Import policy.
