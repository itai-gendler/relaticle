---
entities:
- entity: workspace
  shows:
  - Name
  - Plan
  - Trial Ends
- entity: credit-balance
  shows:
  - Remaining
  - Used
  - Purchased
  - Period Start
  - Period End
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Billing.php
---

# Billing

Published workspace plan, trial, source-derived billing-access information and AI credit allocation.
