# Human Quest Codex Marketplace Guidelines

## Repository Purpose

This repository is the public Codex plugin marketplace for Human Quest
products. It contains installable plugin packaging and agent instructions, not
the private product backends or their generated MCP tool implementations.

## Inner Quest Ownership Boundary

The Inner Quest integration is split across two repositories:

- `humanquest-codex/plugins/inner-quest/` owns the public Codex plugin manifest,
  skill instructions, branding assets, and the hosted MCP endpoint URL.
- The private `inner_quest` application repository owns OAuth, the Personal OS
  API, MCP request handling, generated tool definitions, authorization,
  Firestore access, tests, and production deployment.

Do not copy generated MCP tool schemas or product backend code into this
repository. The plugin discovers its tools from:

`https://www.innerquest.app/api/mcp`

## Current Inner Quest Capability Context

Inner Quest is a typed Personal OS, not only a quest tracker. Its supported
surface includes:

- Self profile and bounded AI context
- Quests, milestones, key results, and check-ins
- Actions and daily practices
- Private reflections and journal records
- Personal contacts, notes, and interactions
- Organizations, people, teams, and work relationships
- Coaching or therapy engagements, sessions, and strategies
- Meetings, notes, transcripts, and summaries
- Career Search preferences, evidence, and sourced opportunities
- Cross-domain timeline and Personal OS search

The MCP intentionally excludes arbitrary Firestore access, authentication
secrets, payment data, infrastructure configuration, email queues, and other
users' records.

## Updating the Inner Quest Plugin

When backend tools change:

1. Implement and test the API/MCP changes in the private `inner_quest`
   repository.
2. Deploy or restart the production MCP server.
3. Verify that MCP `tools/list` advertises the expected tools.
4. Update this repository only when public plugin metadata, skill guidance,
   branding, or marketplace packaging also changed.
5. Refresh or reinstall the plugin connection and start a new Codex task so the
   task receives the updated tool catalog.

Do not bump the plugin version solely because the dynamically discovered server
tool list changed. Bump it when files in the installable plugin bundle change.

## Plugin Conventions

- Plugin manifests: `plugins/{plugin}/.codex-plugin/plugin.json`
- MCP configuration: `plugins/{plugin}/.mcp.json`
- Skills: `plugins/{plugin}/skills/{skill}/SKILL.md`
- Marketplace registration: `.agents/plugins/marketplace.json`
- Hosted MCP endpoints must use HTTPS.
- Never commit credentials, OAuth tokens, API keys, `.env` files, private
  application code, user data, or generated records.
- Keep descriptions and default prompts aligned with the capabilities actually
  exposed by the production MCP server.

## Verification

Before publishing plugin changes:

1. Validate all edited JSON files.
2. Confirm referenced skill and asset paths exist.
3. Compare the source plugin directory with the installed package when
   diagnosing stale local context.
4. Confirm the production MCP tool list separately; the files in this
   repository do not prove that the backend deployment is current.
