---
name: order-printed-cards-shop
description: "Prepare a cart of printed PVC, NFC, MIFARE or wooden cards on the Printags online shop for a person who approves the proof and pays themselves. Use when someone wants a few cards and has no account."
---

# Order printed cards on the Printags shop

The shop (https://studio.printags.com) sells printed PVC, NFC, MIFARE and wooden cards with no account and no minimum order. Its MCP server is https://studio.printags.com/mcp and answers without an account.

You prepare a cart. The person approves the proof (BAT), enters their address and pays on the shop. You never pay, never take an address and never approve a proof.

## Steps

1. List the products first (`list_products`): slugs, minimum quantity, price tiers excluding VAT, cards with an encodable chip. Never use a slug or a price from memory.
2. Announce the total with `quote_cart`. It is indicative (excluding VAT, VAT 20 %, shipping outside France): the payment recalculates it.
3. Artwork, if the person has one: `upload_visual` (file attached to the conversation), `create_upload` (HTTP PUT) or `upload_file` (small file in base64). Each returns an `upload_id`. Without a way to send the file, prepare the cart without artwork: the person sends it from the shop. Never invent artwork. Files: PNG, JPEG or PDF, 25 MB at most.
4. Chip content for encodable products: `encoding` is a link (`uri`) or a `text`. The chip is locked for good once written, as on the shop: tell the person, and pass `lock: false` only if they want to be able to rewrite it. One content per card: `encodings`; one artwork per card (a team): `cards`.
5. `prepare_cart` returns a `claim_url`. Give it to the person: valid 48 hours, usable once, personal. Do not publish it and do not open it yourself. No order exists before the person pays.
6. Later, `get_order_status` with the tracking token the person received after paying.

## Rules

- Invent nothing: quantity, chip content, text and links come from the person. Ask for what is missing.
- Amounts exclude VAT unless stated. Prices fall as the quantity rises.
