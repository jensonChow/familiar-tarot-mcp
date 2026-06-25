# Familiar Tarot — MCP Server

Free tarot for Claude and your AI. **Familiar** gives any MCP client a real tarot
deck: a true shuffle, real card art, upright or reversed, across multiple decks —
then you talk the cards through in chat. A reflective practice, not fortune-telling.

- **Website:** https://familiartarot.com
- **Connect (hosted — no account, no key):** `https://mcp.familiartarot.com/mcp` · transport: `streamable-http`
- **Per-client setup guides:** https://familiartarot.com/connect

> This repository is the public manifest for the **hosted** Familiar Tarot MCP
> server. The server itself runs at `mcp.familiartarot.com` — there is no install
> step. See [`.well-known/mcp/server.json`](.well-known/mcp/server.json).

## What it does

- **Draws real cards** — a verifiable shuffle, not invented by the model.
- **Multiple decks**, real card artwork, upright & reversed meanings.
- **Classic spreads** (Celtic Cross, Past–Present–Future, …) and single-card pulls.
- **Reflective, second-person readings** — reflection, not divination.

## Connect

Add the server URL in your MCP client (Claude Desktop, and any MCP-compatible app):

```
https://mcp.familiartarot.com/mcp
```

No account or API key is required. Step-by-step guides per client:
https://familiartarot.com/connect

## Tools

- `list_decks`, `browse_deck` — explore the available tarot decks
- `shuffle`, `cut`, `draw` — a real, verifiable draw
- `draw_spread`, `draw_situation` — classic spreads and situational layouts
- `list_patterns` — the available spreads and situations

## Links

- Home — https://familiartarot.com
- Cards & meanings — https://familiartarot.com/cards
- Spreads — https://familiartarot.com/spreads
- Support — support@familiartarot.com

---

Familiar is a reflective tarot practice for AI assistants. It does not predict the
future; it offers a structured way to think with the cards.
