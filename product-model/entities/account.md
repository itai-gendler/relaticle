---
references:
- kind: code
  role: implementation
  target: app/Models/User.php
relations:
- entity: workspace
  verb: owns
  cardinality: one-to-many
- entity: membership
  verb: holds
  cardinality: one-to-many
- entity: workspace-invitation
  verb: issues
  cardinality: one-to-many
- entity: access-token
  verb: owns
  cardinality: one-to-many
- entity: conversation
  verb: owns
  cardinality: one-to-many
- entity: import
  verb: starts
  cardinality: one-to-many
- entity: task
  verb: is assigned
  cardinality: many-to-many
- entity: company-creation-proposal
  verb: requests
  cardinality: one-to-many
- entity: person-creation-proposal
  verb: requests
  cardinality: one-to-many
- entity: opportunity-creation-proposal
  verb: requests
  cardinality: one-to-many
- entity: task-creation-proposal
  verb: requests
  cardinality: one-to-many
- entity: note-creation-proposal
  verb: requests
  cardinality: one-to-many
- entity: company-edit-proposal
  verb: requests
  cardinality: one-to-many
- entity: person-edit-proposal
  verb: requests
  cardinality: one-to-many
- entity: opportunity-edit-proposal
  verb: requests
  cardinality: one-to-many
- entity: task-edit-proposal
  verb: requests
  cardinality: one-to-many
- entity: note-edit-proposal
  verb: requests
  cardinality: one-to-many
- entity: record-deletion-proposal
  verb: requests
  cardinality: one-to-many
- entity: custom-field-creation-proposal
  verb: requests
  cardinality: one-to-many
- entity: custom-field-edit-proposal
  verb: requests
  cardinality: one-to-many
- entity: custom-field-options-proposal
  verb: requests
  cardinality: one-to-many
- entity: custom-field-deletion-proposal
  verb: requests
  cardinality: one-to-many
- entity: workspace-invitation-proposal
  verb: requests
  cardinality: one-to-many
- entity: workspace-invitation
  verb: receives
  cardinality: one-to-many
---

# Account

The common personal identity behind the workspace roles. Notification preferences and current web workspace belong to this identity once. Received invitations are resolved by canonical email equality rather than a stored recipient-role column.

## Information kept

- **Name** — The retained display name.
- **Email** — The retained email.
- **Email Verified** — Whether the Account has verified its email identity.
- **Timezone** — The retained timezone.
- **Current Workspace** — The persisted web workspace selection; request binding may temporarily select another workspace in memory.
- **Last Sign-in** — The retained last sign-in.
- **Scheduled Deletion** — The retained scheduled deletion.
- **Task Assignment In-app** — The retained task assignment in-app.
- **Task Assignment Email** — The retained task assignment email.
- **Task Digest Email** — The retained task digest email.
