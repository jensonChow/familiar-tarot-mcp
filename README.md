# Familiar Tarot — a Tarot MCP Server for Claude & your AI

A **tarot MCP server** that gives Claude, ChatGPT, and any MCP-compatible client a
real tarot deck: a true shuffle, real card art, upright or reversed, across multiple
decks — then you talk the cards through in chat. A reflective practice, not
fortune-telling.

It's **hosted** — there is no repo to clone, no `npm install`, no build. You add one
URL and your assistant gains the deck.

- **Website:** https://familiartarot.com
- **Learn more:** https://familiartarot.com/tarot-mcp
- **Server URL (hosted — no account, no API key):** `https://mcp.familiartarot.com/mcp`  ·  transport: `streamable-http`
- **Per-client setup guides:** https://familiartarot.com/connect

> This repository is the public manifest for the **hosted** Familiar Tarot MCP
> server. The server runs at `mcp.familiartarot.com` — see
> [`.well-known/mcp/server.json`](.well-known/mcp/server.json). Published to the
> [official MCP registry](https://registry.modelcontextprotocol.io) as
> `com.familiartarot/tarot`.

## Why a hosted tarot MCP

A language model can write a tarot reading, but it cannot *shuffle* — ask it for a
card and it picks the way it picks the next word, sometimes by what you seem to want
to hear. Familiar removes that: the card is **drawn before it is read**, from a real
shuffle of all seventy-eight (uniform odds — every card a true 1-in-78, upright or
reversed at even chance). What you reflect on is what the deck turned up.

Unlike the open-source tarot MCP projects you install and run yourself, Familiar is
**hosted and maintained** — and it ships **real card artwork** and **multiple decks**
(Rider–Waite–Smith and the public-domain Tarot de Marseille, free), which a
text-only server can't give your assistant.

## What it does

- **Draws real cards** — a verifiable shuffle, not invented by the model.
- **Multiple decks**, real card artwork, upright & reversed.
- **Classic spreads** (Celtic Cross, Past–Present–Future, …), single-card pulls, and
  yes/no draws.
- **Reflective, second-person readings** — reflection, not divination.

## Connect

The server speaks `streamable-http` at:

```
https://mcp.familiartarot.com/mcp
```

No account or API key is required. Pick the path your client supports:

### Clients that add a remote MCP server by URL
**Claude** (claude.ai / Claude Desktop → Customize → Connectors → Add → Add
custom connector), **ChatGPT** (developer mode → connectors), **Le Chat**, and
**Perplexity** — paste the URL above. Step-by-step, per client:
https://familiartarot.com/connect

### Clients that speak stdio (Cursor, Windsurf, and older setups)
Bridge the hosted server with [`mcp-remote`](https://www.npmjs.com/package/mcp-remote):

```json
{
  "mcpServers": {
    "familiar-tarot": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.familiartarot.com/mcp"]
    }
  }
}
```

## Claude skill and Claude Code plugin

The connector gives Claude the deck. The **`familiar-tarot` skill** in
[`skills/familiar-tarot/SKILL.md`](skills/familiar-tarot/SKILL.md) gives it a method:
check that the deck is connected, never invent a card, pick the right draw for the
request (including spreads the deck doesn't name, like a full moon spread), name the
cards before reading them, and close with one question.

**Claude Code** — this repository is a plugin marketplace. Install the skill and the
hosted MCP server together:

```
/plugin marketplace add jensonChow/familiar-tarot-mcp
/plugin install familiar-tarot@familiar-tarot
```

**claude.ai** — add the connector (above), turn on code execution in Settings →
Capabilities, then upload the skill zip in Customize → Skills:
https://familiartarot.com/skills/familiar-tarot.zip · guide:
https://familiartarot.com/claude-tarot-skill

## Example

Once connected, just ask in plain language — the deck is a tool your assistant
reaches for, not a character it plays:

> **You:** Draw three cards on whether to take the new job.
>
> **Claude:** *(calls `draw_spread`)* — Past–Present–Future: **Eight of Pentacles**,
> **The Star** (reversed), **Ace of Wands**. You've been putting in real, careful
> work… *(reads the cards that were actually drawn, then talks them through with you)*

## Tools

- `list_decks`, `browse_deck` — explore the available tarot decks
- `shuffle`, `cut`, `draw` — a real, verifiable draw
- `draw_spread`, `draw_situation` — classic spreads and situational layouts
- `list_patterns` — the available spreads and situations

## Compatible clients

Any MCP client. Confirmed paths: **Claude Desktop**, **Claude.ai**, **ChatGPT**
(developer mode), **Cursor**, **Windsurf**, **Le Chat**, **Perplexity** — and the
official MCP registry / connector directories (Glama, PulseMCP, LobeHub).

## Links

- Home — https://familiartarot.com
- What is a tarot MCP — https://familiartarot.com/tarot-mcp
- Reading tarot with Claude — https://familiartarot.com/claude-tarot-reading
- Claude tarot skill — https://familiartarot.com/claude-tarot-skill
- Cards & meanings — https://familiartarot.com/cards
- Spreads — https://familiartarot.com/spreads
- Support — support@familiartarot.com

## License

The files in this repository (the skill, the plugin manifests and this README) are
MIT-licensed; see [LICENSE](LICENSE). The hosted server, the card art and the
familiartarot.com site are not part of this repository.

---

Familiar is a reflective tarot practice for AI assistants. It does not predict the
future; it offers a structured way to think with the cards.
