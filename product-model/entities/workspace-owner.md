---
acts: external
kind: person
relations:
- entity: account
  verb: has identity
  cardinality: one-to-one
- entity: ai-agent
  verb: connects
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
---

# Workspace Owner

The person who owns a particular workspace; ownership is not a Membership entry.
