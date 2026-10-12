---
references:
- kind: code
  role: implementation
  target: app/Models/Workspace.php
relations:
- entity: membership
  verb: contains
  cardinality: one-to-many
- entity: workspace-invitation
  verb: contains
  cardinality: one-to-many
- entity: company
  verb: contains
  cardinality: one-to-many
- entity: person
  verb: contains
  cardinality: one-to-many
- entity: opportunity
  verb: contains
  cardinality: one-to-many
- entity: task
  verb: contains
  cardinality: one-to-many
- entity: note
  verb: contains
  cardinality: one-to-many
- entity: custom-field
  verb: contains
  cardinality: one-to-many
- entity: activity
  verb: contains
  cardinality: one-to-many
- entity: import
  verb: contains
  cardinality: one-to-many
- entity: credit-balance
  verb: has balance
  cardinality: one-to-one
- entity: conversation
  verb: contains
  cardinality: one-to-many
- entity: access-token
  verb: contains
  cardinality: one-to-many
---

# Workspace

The customer’s tenant, containing CRM records and its membership. Its owner is kept independently of Membership.

## Information kept

- **Name** — The retained display name.
- **Handle** — The retained handle.
- **Logo** — The retained logo.
- **Personal Workspace** — The retained personal workspace.
- **Use Case** — The retained use case.
- **Use Case Context** — The selected context entries valid for the chosen Use Case.
- **Other Use Case** — The optional free-text response for Other, at most 120 characters; cleared for other use cases.
- **Setup Step** — The retained setup step.
- **Referral Source** — The retained referral source.
- **Referral Detail** — The retained referral detail.
- **Referral Prompt** — The retained referral prompt.
- **Plan** — The retained plan.
- **Trial Ends** — The retained trial ends.
- **Scheduled Deletion** — The retained scheduled deletion.

## States

### Active

The instance is available in its ordinary workspace context.

### Scheduled for Deletion

A deletion deadline is retained; eventual purge is a separate lifecycle.
