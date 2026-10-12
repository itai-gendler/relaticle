---
appliesTo:
- type: capability
  id: browse-help
- type: entity
  id: product-configuration
  facts:
  - Documentation Enabled
references:
- kind: code
  role: implementation
  target: packages/Documentation/src/Http/Controllers/HelpController.php
- kind: code
  role: implementation
  target: app/Features/Documentation.php
---

# Help requires enabled Documentation

The shipped help library, article and search controller is available while Documentation Enabled is active. Disabled requests return not found/disabled. Shipped articles do not become customer Article instances.
