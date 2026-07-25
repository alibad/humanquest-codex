---
name: inner-quest
description: Manage the Inner Quest Personal OS through typed MCP tools for self context, quests, actions, private reflections, personal relationships, organizations and work relationships, coaching or therapy, meetings and transcripts, check-ins, timeline, and cross-domain search. Use when Codex needs to review, search, create, update, or delete the user's explicitly authorized Inner Quest records.
---

# Inner Quest

Use the Inner Quest MCP tools for all account data. Do not reproduce HTTP requests or expose authentication values.

## Operating rules

- Prefer read-only tools when the user asks to review, summarize, search, or plan.
- Create or change records only when the user asks for the change.
- Delete a record only when the user explicitly asks to delete that exact record. Resolve ambiguous names to IDs first.
- Preserve pagination cursors and continue only when more results are needed.
- Use ISO dates (`YYYY-MM-DD`) and API enum values exactly as declared by each tool.
- Link new actions to a quest with the `parent` field when the relationship is known.
- Use the unified timeline for recent activity across resource types. Use typed list tools for resource-specific filtering.
- Use Personal OS search when the user names a topic or person but not a resource type. Use the capability manifest when the available domain or operation is unclear.
- Treat private reflections, relationship notes, coaching or therapy records, and meeting transcripts as highly sensitive. Return only the details needed for the user's request.
- Never claim arbitrary database access. The MCP exposes typed, user-owned domains and deliberately excludes authentication secrets, payment state, provider credentials, and meeting audio blobs.
- If authentication is missing, ask the user to select **Connect Inner Quest**, sign in through the browser, and approve access. Never ask for an API key, environment variable, or Terminal command.

## Common workflows

### Progress review

1. List active quests.
2. List open actions, optionally filtered to a quest.
3. Read recent quest check-ins when readiness or momentum matters.
4. Summarize progress, blockers, and concrete next steps.

### Capture a reflection

1. Confirm or infer the reflection type and relevant date.
2. Add quest, action, or contact links when the relationship is clear.
3. Create the reflection.
4. Return the created record and note that AI insights may populate asynchronously.

### Plan a quest

1. Create the quest with a concise title, purpose, category, and measurable outcomes when available.
2. Add actions separately and attach them through `parent`.
3. Read the resulting quest before presenting the plan so IDs and relationships are grounded in server data.

### Relationship briefing

1. Search for or list the contact and resolve the exact ID.
2. Read the contact's notes, interactions, preferences, relationship assessments, and growth context relevant to the request.
3. Search linked reflections or meetings only when they materially improve the briefing.
4. Summarize with discretion and distinguish stored facts from interpretation.

### Work context

1. Resolve the organization.
2. Read the relevant people, reporting lines, teams, projects, roles, and interaction notes.
3. Use exact organization and person IDs for updates.
4. Avoid exposing unrelated coworker information in the response.

### Coaching or meeting review

1. Resolve the engagement, session, strategy, or meeting record.
2. Read only the relevant notes, transcript sections, summaries, homework, or coaching analysis.
3. When creating homework, preserve the server-provided link to the unified action item.
4. Confirm the exact record before any destructive change.
