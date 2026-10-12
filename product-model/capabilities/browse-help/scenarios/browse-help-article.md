---
kind: primary
routes:
  main: Read help article
steps:
- text: Request the help article
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::public::help-article
  actor: visitor
- text: The Product returns the shipped help information
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::public::help-article
  actor: visitor
references:
- kind: code
  role: implementation
  target: packages/Documentation/src/Http/Controllers/HelpController.php
---

# Read help article

## Trigger

Documentation is enabled and a Visitor requests the help article.

## Outcome

The shipped article and related information are available.
