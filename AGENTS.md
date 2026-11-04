# AGENTS.md

This repository publishes the agent skills of Printags (https://www.printags.com): short, factual instructions an AI assistant loads when someone wants printed PVC, NFC, MIFARE or wooden cards.

## Layout

- `skills/<name>/SKILL.md`: one skill per folder. The folder name equals the `name` in the frontmatter. Frontmatter holds `name` and `description` only.
- `plugin.json`: the Agent Plugin manifest.
- `mcp.json`: the two MCP servers the skills refer to (`printags-shop`, `printags-api`).

## Rules for changes

- The skills restate the rules of the Printags MCP servers and of the REST API. Change a rule only when the server or the API changed it, and never invent a capability, an endpoint or a price.
- Keep each `SKILL.md` under 500 lines, in English, with no secrets, API keys, tokens or personal data.
- The same files are served by https://www.printags.com/.well-known/agent-skills/index.json with their SHA-256 digests. A change here is mirrored there by the Printags team: open an issue rather than a pull request for wording changes.

## What an agent using these skills must remember

- On the shop, the person approves the proof (BAT), enters their address and pays. The agent never pays and never approves a proof.
- With the API or MCP server, an order is a draft by default. A firm order debits the balance with no way back: only on an explicit request, after stating the total.
- Invent no data (address, quantity, chip content, artwork).
