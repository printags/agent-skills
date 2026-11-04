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

## Where else to find them

- Skills index: https://www.printags.com/.well-known/agent-skills/index.json
- MCP servers: shop https://studio.printags.com/mcp, API https://mcp.printags.com
- OpenAPI document: https://www.printags.com/openapi.json
- Documentation: https://docs.printags.com
- Prices in Markdown: https://www.printags.com/pricing.md
