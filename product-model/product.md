---
id: relaticle
summary: Workspace CRM with Companies, People, Opportunities, Tasks, Notes and Rela-assisted proposed changes.
category: customer-relationship-management
languages:
- en
limitations:
- Rela saves no record change itself; each suggested write waits for the requesting person's decision.
- An External AI Agent acts with its person's credential in one Workspace, outside Rela's proposal review.
- Deleted records stay restorable; only Workspace owners and admins remove them permanently.
- Rela responses draw on the Workspace's shared AI credit allowance; other CRM work spends no credits.
- The product ships in English; other languages are left to self-hosted translations.
references:
- kind: code
  role: implementation
  target: README.md
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: packages/Chat/src/Agents/CrmAssistant.php
---

# Relaticle

Relaticle keeps workspace Companies, People, Opportunities, Tasks and Notes, their relationships and configured values. People work directly or ask Rela to read records and retain proposed changes for a personal decision. The customer workspace also offers membership administration, imports, activity, access tokens, notification preferences and billing information.

## Intent

Help a workspace keep its customer relationships and follow-up work together while making proposed writes visible before they are accepted.
