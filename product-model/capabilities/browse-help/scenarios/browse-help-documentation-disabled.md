---
kind: validation
routes:
  main: Documentation disabled
steps:
- text: The installation documentation switch is disabled.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::public::help-library
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::public::help-library
  actor: visitor
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::public::help-library
  actor: visitor
references:
- kind: code
  role: implementation
  target: packages/Documentation/src/Http/Controllers/HelpController.php
---

# Documentation disabled

## Trigger

The installation documentation switch is disabled.

## Outcome

The help request returns its disabled/not-found outcome rather than a help article.
