# FiLot MCP

A remote MCP server for gold prices and gold-bar records. Read-only, public, no authentication.

- Endpoint: `https://mcp.filot.me/mcp` (streamable HTTP, JSON-RPC by POST)
- Alternate endpoint: `https://api.filot.me/functions/v1/filot-mcp`
- Documentation: https://filot.me/ai-assistants/
- Registry name: `me.filot/gold`

## Tools

| Tool | What it answers |
|---|---|
| `world_gold_price` | Today's world (spot) gold price per gram, troy ounce and kilogram, in any currency |
| `gold_price_on_date` | The world gold price on a past date, for a tax return, an inheritance or a purchase record |
| `gold_buyback_prices` | What Indonesian dealers pay today for one bar of a given brand and weight, in rupiah, set beside the world value of the gold; an optional `offer_idr` (a price someone offered) is compared in numbers only |
| `gold_price_sources` | Which dealer sites FiLot reads, and the latest price day of each |
| `indonesian_gold_tax` | Indonesian tax facts for physical gold: PPN, PPh 22, thresholds, and what applies to a buyer or a seller |
| `gold_zakat` | Zakat on gold: nisab, rate and due date |
| `verify_gold_bar_record` | Checks a FiLot gold bar record against the public Solana blockchain |

## Example

    curl -s -X POST https://mcp.filot.me/mcp \
      -H 'Content-Type: application/json' \
      -H 'Accept: application/json, text/event-stream' \
      -d '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'

## Notes

- Read-only: no wallet actions, no money movement, no account.
- Prices are computed by fixed rules, not by an AI model.
- Tax and zakat answers are facts, not advice.
- Indonesian dealer sites that block AI crawlers are excluded from `gold_buyback_prices`.

## About FiLot

FiLot is a chat-first companion for physical gold and Solana DeFi: it keeps a record of what each bar cost, tracks it against the gold price, and checks bar records on-chain. https://filot.me
