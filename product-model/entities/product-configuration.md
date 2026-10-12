---
references:
- kind: code
  role: implementation
  target: config/relaticle.php
- kind: code
  role: implementation
  target: packages/Chat/config/chat.php
- kind: code
  role: implementation
  target: packages/ImportWizard/config/import-wizard.php
singleton: true
---

# Product Configuration

The installation’s actual switches, configured limits and durations.

## Information kept

- **Billing Enabled** — The retained billing enabled.
- **Documentation Enabled** — The retained documentation enabled.
- **Setup Conversation Enabled** — The retained setup conversation enabled.
- **Email Integration Enabled** — The retained email integration enabled.
- **Maximum Owned Workspaces** — The configured maximum owned-workspace count, default 10.
- **Deletion Grace Days** — The configured deletion grace, default 30 days.
- **Maximum Batch Size** — The configured record write batch limit, default 25.
- **Maximum Plan Steps** — The configured maximum linked proposal steps, default six.
- **Ordinary Proposal Minutes** — The ordinary proposal lifetime, configured as 1,440 minutes.
- **Setup Proposal Minutes** — The setup-conversation proposal lifetime, configured as 10,080 minutes.
- **Maximum Fields Per Record Type** — The configured field-definition limit, default 50.
- **Maximum Field Options** — The configured choice-option limit, default 50.
- **Maximum Import Rows** — The import row limit, configured as 10,000.
- **Maximum Import Bytes** — The import upload size limit, configured as 10 MiB.
