---
appliesTo:
- type: entity
  id: workspace-invitation-proposal
  effect: changes
  to: Accepted
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Enums/ProposalEntity.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
---

# Invitations require their own acceptance

Invitation proposals remain pending during plan bulk approval and its keyboard shortcut. Their own decision sends the invitation entries. This does not describe uninspected email-send proposals.
