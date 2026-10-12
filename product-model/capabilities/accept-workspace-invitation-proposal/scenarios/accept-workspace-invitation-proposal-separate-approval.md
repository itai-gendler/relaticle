---
kind: edge
routes:
  main: Invitation requires its own decision
steps:
- text: Approve the invitation separately
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product resolves only the separately approved invitation step
  kind: product
  entities:
  - entity: workspace-invitation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    - Results
    from: Proposed
    to: Accepted
  - entity: workspace-invitation
    effect: creates
    facts:
    - Email
    - Role
    - Inviter
    - Workspace
    - Issued At
    - Expires At
    - Invitation Credential
    to: Issued
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Enums/ProposalEntity.php
---

# Invitation requires its own decision

## Trigger

A plan contains an invitation proposal beside ordinary CRM proposals.

## Outcome

Bulk plan approval leaves the invitation pending. Its own approval issues the addressed invitations and retains the actual send result; a keyboard bulk shortcut cannot send it.
