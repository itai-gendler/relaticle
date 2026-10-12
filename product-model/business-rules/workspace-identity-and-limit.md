---
appliesTo:
- type: entity
  id: workspace
  effect: creates
- type: entity
  id: workspace
  effect: changes
  facts:
  - Name
  - Handle
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/CreateWorkspace.php
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
- kind: code
  role: implementation
  target: app/Rules/ValidWorkspaceSlug.php
---

# Workspace identity is valid and ownership respects its maximum

Name is required and at most 255 characters. Explicit handles are valid unique unreserved lowercase word-and-dash values; omitted handles settle inside insertion. The actual owned-workspace count includes scheduled workspaces and must be below the configured default-ten maximum; invited memberships do not count. First ownership sets Personal Workspace. Referral detail/prompt validation follows the chosen source.
