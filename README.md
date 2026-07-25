# Human Quest for Codex

Official Codex plugins for Human Quest products.

This repository is a public plugin marketplace. Product backends, private application code, user data, and credentials remain in their respective private repositories.

## Available plugins

### Plan Quest

Connect Codex and ChatGPT securely to Plan Quest to review plans, priorities,
backlog items, milestones, key results, mind maps, history, and collaborators,
then make bounded updates with explicit permissions.

- Website: [plans.quest](https://www.plans.quest)
- Authentication: OAuth 2.1 browser sign-in
- MCP server: hosted by Plan Quest
- API keys or local environment variables: not required

### Inner Quest

Connect Codex securely to the Inner Quest Personal OS. Work with self context,
quests, actions, private reflections, personal and work relationships,
organizations, coaching or therapy records, meetings, check-ins, the unified
timeline, Career Search preferences and evidence, sourced career opportunities,
and cross-domain search through typed, user-owned operations.

- Website: [innerquest.app](https://www.innerquest.app)
- Authentication: OAuth 2.1 browser sign-in
- MCP server: hosted by Inner Quest
- API keys or local environment variables: not required

The plugin package contains public metadata, agent instructions, branding, and
the hosted MCP URL. The private Inner Quest application owns the API, OAuth,
generated MCP tools, authorization, data access, tests, and production
deployment. Tool definitions are discovered dynamically from the hosted server;
they are not copied into this marketplace repository.

## Install from this marketplace

Clone the repository:

```bash
git clone https://github.com/alibad/humanquest-codex.git
```

Add the cloned repository as a Codex marketplace:

```bash
codex plugin marketplace add /absolute/path/to/humanquest-codex
```

Install Inner Quest:

```bash
codex plugin add inner-quest@humanquest
```

Install Plan Quest:

```bash
codex plugin add plan-quest@humanquest
```

Start a new Codex task, select the installed plugin, sign in through the
browser, and approve access.

## Updating MCP capabilities

When Inner Quest adds or changes MCP tools:

1. Deploy the corresponding backend changes from the private Inner Quest
   application repository.
2. Confirm the production MCP server advertises the updated tool list.
3. Update this marketplace only when the plugin manifest, skill guidance,
   branding, or packaging also needs to change.
4. Refresh or reinstall the plugin connection.
5. Start a new Codex task so it receives the refreshed tool catalog.

An existing task may continue to show the tool catalog that was loaded when the
task started. A stale task does not necessarily mean the marketplace source or
production MCP server is stale.

## Repository layout

```text
AGENTS.md
.agents/plugins/marketplace.json
plugins/
  plan-quest/
    .codex-plugin/plugin.json
    .app.json
    assets/
  inner-quest/
    .codex-plugin/plugin.json
    .mcp.json
    assets/
    skills/
```

Each plugin has its own manifest, assets, skills, MCP configuration, and release version. New Human Quest products can be added as sibling directories under `plugins/` and registered in the marketplace file.

## Security

- Never commit API keys, OAuth tokens, Firebase credentials, `.env` files, or user data.
- Plugins should point to hosted production services over HTTPS.
- Authentication must happen through the product's supported connection flow.
- Report security issues privately through the contact channel listed on the relevant product website.
