---
name: printags-integrator-api
description: "Price, order and track printed cards for a business or integrator with the Printags REST API or MCP server, shipped white-label. Use for orders created from software, with artwork, chip encoding data and tracking."
---

# Order cards for customers with the Printags API or MCP server

For a business or an integrator that produces cards for its own customers. Printags prints and encodes the cards and ships them white-label.

## Access

- REST API: https://api.printags.com, OpenAPI document at https://www.printags.com/openapi.json (YAML: https://www.printags.com/openapi.yaml), authentication by Bearer token (the account's API key). Documentation: https://docs.printags.com.
- MCP server: https://mcp.printags.com, by signing in to a Printags account (OAuth) or with the API key in an `Authorization: Bearer` header. Free on every plan.
- Sandbox: a test key (prefix `sk_test_`) creates test orders that are neither charged nor manufactured. Say so to the person when the account is in test mode.

## Ordering N cards

1. Read the catalogue of models (never an identifier from memory) and, if the person wants one, the packagings.
2. Compare prices with the estimate and read the carriers and their delays. The exact amount a firm order would debit on this account comes from `quote_order`, not from the estimate. All amounts exclude VAT.
3. Artwork: upload a file and cite its id as the front and back visuals. Never invent artwork.
4. Chip content: a link (`uri`), a text or dynamic content. Without it the chip is not encoded. Locking the chip is permanent: only when the person asks.
5. Create the order. A draft is the default: nothing is printed or charged and the person validates it in the dashboard. A firm order (`draft: false`) starts production and debits the balance with no way back: only on an explicit request, after stating the total and the balance and getting agreement. When unsure, draft.
6. Pass an idempotency key (a UUID you generate) when creating an order through MCP: after an error or a timeout, retry with the same key and you find the order already created instead of charging a second one.
7. Track the order: status, history, parcel and tracking number. A `validated` or `in_queue` status is not `shipped`: promise no delivery date.

## Rules

- Invent no data: address, phone, e-mail, quantity, chip content. Ask for what is missing.
- Addresses: name and street 38 characters at most, city 35, letters, digits, space and `- . _ '` only. Shorten without changing the meaning.
- With several accounts, ask the person which one to act on and name it before any debit. Keep the same account for the artwork, the order and its tracking.
