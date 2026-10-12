---
appliesTo:
- type: entity
  id: workspace-invitation
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/InviteWorkspaceMember.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/ResendWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Http/Controllers/AcceptWorkspaceInvitationController.php
---

# Invitations preserve addressed identity and credential validity

Issuance canonicalizes email and validates role, duplicates and rate limits, storing a hashed opaque credential with seven-day expiry and queueing mail after commit. Resend rotates credential/expiry under its one-minute guard. Acceptance requires verified signed-in canonical email equality, valid locked invitation and neither Account nor Workspace scheduled for deletion. A concurrent already-member acceptance succeeds without duplicating Membership. Acceptance, decline and revocation remove the invitation.
