---
kind: primary
routes:
  main: Change membership role
steps:
- text: Save the new joined role role
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
- text: The Product saves the chosen role
  kind: product
  entities:
  - entity: membership
    effect: changes
    facts:
    - Role
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/UpdateWorkspaceMemberRole.php
---

# Change membership role

## Trigger

The actor selects a member’s new assignable non-Admin role.

## Outcome

The Membership retains the chosen role; any operation touching old or new Admin status retains its separate owner check.
