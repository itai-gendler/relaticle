---
availability:
- place: customer-web::public
references:
- kind: code
  role: implementation
  target: routes/web.php
- kind: code
  role: implementation
  target: app/Http/Controllers/ContactController.php
- kind: code
  role: implementation
  target: packages/Documentation/src/Http/Controllers/HelpController.php
---

# Browse help

Read or search the shipped help library and open an article when documentation is enabled.
