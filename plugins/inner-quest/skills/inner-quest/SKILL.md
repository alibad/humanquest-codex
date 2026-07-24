---
name: inner-quest
description: Manage personal goals and self-development data in Inner Quest through quests, actions, reflections, quest check-ins, and the unified timeline. Use when Codex needs to review progress, plan or update meaningful challenges, manage next actions, capture journal entries or insights, inspect readiness check-ins, or summarize recent Inner Quest activity.
---

# Inner Quest

Use the Inner Quest MCP tools for all account data. Do not reproduce HTTP requests or expose authentication values.

## Operating rules

- Prefer read-only tools when the user asks to review, summarize, search, or plan.
- Create or change records only when the user asks for the change.
- Delete a quest, action, or reflection only when the user explicitly asks to delete that exact record. Resolve ambiguous names to IDs first.
- Preserve pagination cursors and continue only when more results are needed.
- Use ISO dates (`YYYY-MM-DD`) and API enum values exactly as declared by each tool.
- Link new actions to a quest with the `parent` field when the relationship is known.
- Use the unified timeline for recent activity across resource types. Use typed list tools for resource-specific filtering.
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
