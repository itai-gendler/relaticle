---
kind: validation
routes:
  main: Wrong account
steps:
- text: "The invitation email does not match the signed-in identity\u2019s canonical email."
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Http/Controllers/AcceptWorkspaceInvitationController.php
---

# Wrong account

## Trigger

The invitation email does not match the signed-in Account’s canonical email.

## Outcome

The matching-identity failure is shown without membership creation or consuming the invitation.
