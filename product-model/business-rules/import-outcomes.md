---
appliesTo:
- type: entity
  id: import
- type: entity
  id: failed-import-row
- type: capability
  id: import-records
references:
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Jobs/ExecuteImportJob.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Support/MatchResolver.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Livewire/Steps/ReviewStep.php
- kind: code
  role: implementation
  target: packages/ImportWizard/src/Support/EntityLinkStorage/MorphToManyStorage.php
---

# Import matching and per-row failures preserve completed work

CSV/text input respects configured 10-MB/10,000-row limits and rejects empty input or duplicate headers. Required mappings and unresolved matches block execution. Review corrections apply to matching raw column values. Company/Person match through ID/domain/email/phone choices; Opportunity/Task by ID; Notes create. Matched native updates keep filled values rather than treating blanks as clearing. Match-only unmatched or unsupported-match rows skip. Execution restores the original creator/workspace, commits each row and checkpoints progress/counters after configured-value storage. Failed originals keep errors; successful rows remain. Related collections attach additively.
