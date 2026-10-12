---
scope: Inspected customer CRM, REST and MCP record operations, Chat, workspace settings,
  import process, public help/contact and billing-access code.
method: Static entry-point, handler/query/action, persistence, guard and observable-outcome
  inspection at commit 8deec701b010fad06e4f7bff0bd6640102d7a391.
covered:
- description: CRM action, model, policy and customer resource subareas
  paths:
  - app/Actions/Company/
  - app/Actions/People/
  - app/Actions/Opportunity/
  - app/Actions/Task/
  - app/Actions/Note/
  - app/Models/
  - app/Policies/
  - app/Filament/Resources/
- description: Shared CRM list, filter, sort and workspace-context code
  paths:
  - app/Queries/
  - app/Support/CurrentWorkspace.php
  - app/Http/Middleware/SetApiWorkspaceContext.php
- description: Inspected REST record controllers, requests and serializers
  paths:
  - app/Http/Controllers/Api/V1/
  - app/Http/Requests/Api/V1/
  - app/Http/Resources/V1/
  - routes/api.php
- description: Inspected MCP CRM, definition, context and activity code
  paths:
  - app/Mcp/Tools/
  - routes/ai.php
- description: Inspected conversation, proposal, decision and credit code
  paths:
  - packages/Chat/src/
  - packages/Chat/resources/js/chat/
- description: Workspace creation, use-case setup, membership and scheduling code
  paths:
  - app/Actions/Jetstream/
  - app/Actions/Onboarding/
  - app/Livewire/App/Workspaces/
  - app/Filament/Pages/
- description: Personal token, notification and hosted billing-access subareas
  paths:
  - app/Livewire/App/AccessTokens/
  - app/Actions/User/UpdateNotificationPreferences.php
  - app/Services/Notifications/
  - app/Console/Commands/SendTaskDigestCommand.php
  - app/Services/Billing/HostedWorkspaceAccess.php
- description: Import upload, mapping, value review, preview, execution, restart and
    output code
  paths:
  - packages/ImportWizard/src/
- description: Inspected public information, contact and help code
  paths:
  - routes/web.php
  - app/Http/Controllers/ContactController.php
  - packages/Documentation/src/Http/Controllers/HelpController.php
- description: Inspected Activity query dispatch, workspace boundaries, retained membership
    assignments and fixed-role authorization code
  paths:
  - packages/Chat/src/Tools/Activity/ListActivityTool.php
  - app/Mcp/Tools/ListActivityTool.php
  - app/Filament/Pages/Workspace/ActivityLog.php
  - app/Models/Membership.php
  - app/Enums/WorkspaceRole.php
exclusions:
- description: Mapping instructions, CI, development and build machinery and test
    machinery
  paths:
  - ".agents/"
  - ".github/"
  - tests/
- description: Visual assets and layout styling
  paths:
  - resources/css/
unmapped:
- description: Email and calendar connection, sync, privacy, sharing and tool code
  paths:
  - packages/EmailIntegration/
  - app/Mcp/Tools/Email/
  - packages/Chat/src/Tools/Email/
- description: Internal administration, support and impersonation code
  paths:
  - packages/SystemAdmin/
  - app/Http/Controllers/Impersonation/
- description: Complete account security and OAuth consent or revocation code
  paths:
  - app/Http/Controllers/Auth/
  - app/Http/Controllers/Mcp/
  - app/Livewire/UpdateProfileInformationForm.php
- description: Checkout, purchased credits, subscription, webhook and portal lifecycle
    code
  paths:
  - app/Actions/Billing/
  - app/Http/Controllers/Billing/
- description: Field type settings and rich-content or media lifecycle code
  paths:
  - app/Filament/CustomFields/
  - app/Http/Controllers/Media/
- description: REST upsert and user endpoint code
  paths:
  - app/Http/Controllers/Api/V1/CompaniesUpsertController.php
  - app/Http/Controllers/Api/V1/PeopleUpsertController.php
  - app/Http/Resources/V1/UserResource.php
- description: Untraced aggregate and search operations
  paths:
  - app/Queries/Crm/
  - app/Mcp/Tools/AggregateOpportunitiesTool.php
  - packages/Chat/src/Tools/AggregateCrmTool.php
- description: Transcription, feedback, attachment, regeneration and omitted proposal
    code
  paths:
  - packages/Chat/src/Http/Controllers/TranscribeController.php
  - packages/Chat/src/Http/Controllers/MessageFeedbackController.php
  - packages/Chat/src/Http/Controllers/ChatAttachmentController.php
  - packages/Chat/src/Tools/Workspace/RemoveSampleDataTool.php
- description: Email-enabled setup and full sample-generation code
  paths:
  - app/Actions/Onboarding/
  - packages/OnboardSeed/
- description: Import recovery, retention, cleanup and executing-cancellation code
  paths:
  - packages/ImportWizard/src/Filament/Pages/ImportHistory.php
  - packages/ImportWizard/src/Commands/
  - packages/ImportWizard/src/Livewire/ImportWizard.php
- description: Eventual workspace purge and post-leave destination code
  paths:
  - app/Actions/Jetstream/DeleteWorkspace.php
  - app/Livewire/App/Workspaces/WorkspaceMembers.php
- description: Additional marketing, blog, comparison and developer documentation
    distribution
  paths:
  - app/Http/Controllers/ComparisonController.php
  - app/Http/Controllers/AlternativesController.php
  - packages/Documentation/src/Http/Controllers/DocumentationController.php
  - packages/Documentation/src/Http/Controllers/OpenApiSpecController.php
limitations:
- description: Native resource save side effects depend on partially inspected framework
    and custom-field implementations
  paths:
  - app/Filament/Resources/
  - app/Filament/CustomFields/
- description: Cashier cleanup and payment failure lifecycle extends beyond inspected
    access derivation
  paths:
  - app/Services/Billing/
  - app/Models/Workspace.php
---

# Coverage
