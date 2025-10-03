Overview

What it is
A spreadsheet-database hybrid with relational tables, views, automations, interfaces, and an HTTP API. Great as a lightweight CRM/OPS backend for SMB workflows.

When to use
Prototype/operate business workflows (leads, intake, onboarding, content, projects) where non-technical users need to see/edit data and automations need to run with minimal ops overhead.

When not to use
Heavy analytics, high-volume event streams, complex joins, or strict transactional guarantees → use a real DB (Postgres) + app.

Core Concepts

Workspace / Base / Table / Record / Field
Workspaces contain bases (apps). Each base has tables (like DB tables). Rows are records; columns are fields.

Field types
Single line text, Long text, Number, Currency, Percent, Date/Time, Checkbox, Single/Multi-select, Attachment, Formula, Rollup, Lookup, Link to another record, Collaborator, Rating, URL, Email, Phone.

Views
Saved filters/sorts/grouping: Grid, Kanban, Calendar, Gallery, Timeline. Views drive permissions + interfaces + automations.

Linked Records
Airtable’s “foreign key”. Enables Rollup/Lookup fields for denormalized dashboards.

Automations (No-Code)

Triggers: record created/updated, enters view, at schedule, form submitted, webhook received.

Actions: create/update record, send email, post to Slack/Teams, call Run script, call webhook/HTTP request.

Patterns for SMBs

Lead enters “New” → create follow-up task + send confirmation email

No activity in 48h → notify owner + escalate

Stage changes to “Won” → generate invoice draft + handoff to onboarding

Scripting & API

Scripting (in-product): JS runtime with input.config(), base.getTable(), table.createRecordsAsync(), etc.


Example Schemas (SMB-Ready)
1) Lead Tracking / Mini-CRM

Leads

Fields: Name, Company, Source (Single-Select), Stage (New/Contacted/Qualified/Won/Lost), Owner (Collaborator), Next Action (Date), Last Touch (Date), Email, Phone, Notes (Long text)
Activities

Fields: Lead (Link), Type (Call/Email/Meeting), When (DateTime), Notes, Owner
Rollups/Lookups

In Leads: Last Activity Date (Rollup MAX of Activities.When) → drive stale-lead alerts.

2) Client Intake/Onboarding (Law/Dental/Agency)

Clients: Name, Status (Intake/Contract/Onboarding/Active), Assigned Team, Docs Received (Checkbox/Rollup)
Tasks: Client (Link), Task, Due, Owner, Done (Checkbox)
Automations: status → email templates + Slack handoff.

Security & Limits (Reality Check)

Permissions: workspace/base level; view share links can be read-only or editable (be careful).

PII/PHI: Avoid storing sensitive health data unless you’ve verified compliance needs; Airtable is not a HIPAA BA by default.

API limits: Pagination (100 records/page). Rate limits depend on plan—batch writes recommended.

Record limits: Base record caps and attachment storage caps vary by plan; design for archival and pruning.

AI Workflow Patterns (Practical)
Draft Follow-Up Email (OpenAI via n8n)

Trigger: Lead stage = Contacted, no response in 48h

Action: OpenAI chat.completions with prompt:

System: You write concise, professional follow-ups for SMBs.
User: Draft a 90-word follow-up referencing:
- Name: {{ $json.name }}
- Company: {{ $json.company }}
- Last Touch Date: {{ $json.last_touch }}
- Offer: Free 15-min consult
Constraint: Warm tone, 1 CTA, no fluff.


Save result to {Draft Email} field → optional human approval → send.

Lead Qualification (Scoring)

Inputs: {Company Size}, {Industry}, {Source}, {Engagement}

Output (Formula/AI): Score 0–100 + Tier (A/B/C) → filter views & automations.

REST API: Per-base endpoints. Auth via Bearer token. Rate-limit friendly; plan-dependent caps.
