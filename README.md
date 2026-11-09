# Printags agent skills

[![skills.sh](https://skills.sh/b/printags/agent-skills)](https://skills.sh/printags/agent-skills)

Agent skills for [Printags](https://www.printags.com), which prints and encodes PVC, NFC, MIFARE and wooden cards and ships them white-label.

| Skill | Use it when |
|---|---|
| [`order-printed-cards-shop`](skills/order-printed-cards-shop/SKILL.md) | someone wants a few printed cards and has no account: the assistant prepares a cart on the online shop, the person approves the proof and pays |
| [`printags-integrator-api`](skills/printags-integrator-api/SKILL.md) | a business or integrator orders cards for its own customers with the REST API or the MCP server |

## Install

```sh
npx skills add printags/agent-skills
```

## Printags MCP servers

Printags runs three remote MCP servers (Streamable HTTP), listed in the [official MCP registry](https://registry.modelcontextprotocol.io/v0.1/servers?search=com.printags) under `com.printags/*`.

| Server | Endpoint | Auth | What it does |
|---|---|---|---|
| Printags shop (`com.printags/shop`) | `https://studio.printags.com/mcp` | none | Lists the shop's cards and prices, quotes a cart, uploads the artwork and prepares a cart. The person opens a link, approves the proof and pays on the shop. 7 tools. |
| Printags (`com.printags/mcp`) | `https://mcp.printags.com` | OAuth or API key | For businesses and integrators with a Printags account: catalogue, price and shipping estimates, artwork upload, draft orders, order tracking. Free on every plan. 13 tools. |
| Printags docs (`com.printags/docs`) | `https://www.printags.com/mcp/docs` | none | Searches and reads the pages of printags.com. Read-only. 2 tools. |

[![Printags shop MCP connector](https://glama.ai/mcp/connectors/com.printags/shop/badges/score.svg)](https://glama.ai/mcp/connectors/com.printags/shop)
[![Printags docs MCP connector](https://glama.ai/mcp/connectors/com.printags/docs/badges/score.svg)](https://glama.ai/mcp/connectors/com.printags/docs)

Add a server in Claude Code:

```sh
claude mcp add --transport http printags-shop https://studio.printags.com/mcp
claude mcp add --transport http printags https://mcp.printags.com
```

Other clients: [`mcp.json`](mcp.json), or the setup guide at https://www.printags.com/en/mcp-server/.

## Where else to find them

- Skills index: https://www.printags.com/.well-known/agent-skills/index.json
- MCP servers: shop https://studio.printags.com/mcp, API https://mcp.printags.com, docs https://www.printags.com/mcp/docs
- OpenAPI document: https://www.printags.com/openapi.json
- Documentation: https://docs.printags.com
- Prices in Markdown: https://www.printags.com/pricing.md
