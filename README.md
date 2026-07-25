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

Connect Codex securely to Inner Quest to review and manage quests, actions, reflections, check-ins, and timeline items.

- Website: [innerquest.app](https://www.innerquest.app)
- Authentication: OAuth 2.1 browser sign-in
- MCP server: hosted by Inner Quest
- API keys or local environment variables: not required

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

## Repository layout

```text
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
