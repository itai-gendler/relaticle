---
kind: configuration
of: capability-scenario
settings:
- entity: product-configuration
  fact: Email Integration Enabled
takesEffect: When the Workspace is created, its first Setup Step is fixed as Email or Use Case.
stability: A Workspace already in setup keeps its retained Setup Step. If Email Integration is turned off while a Workspace is at Email or Sharing, opening setup moves it to Use Case.
alternatives:
- id: set-up-workspace-use-case
  selectedWhen: Email Integration Enabled is off, so setup begins at Use Case. Off is the default.
- id: set-up-workspace-mailbox
  selectedWhen: Email Integration Enabled is on, so setup begins at Email with the mailbox and sharing steps.
---

# Workspace setup with or without a mailbox

Each installation chooses whether new Workspaces start setup by connecting the owner's mailbox; both setup forms are supported.
