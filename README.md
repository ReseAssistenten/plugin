# ReseAssistenten — Claude plugin

> **Svenska:** ReseAssistenten-pluginet kopplar Claude till ditt eget ReseAssistenten-konto
> så att assistenten kan planera award-resor med SAS, köra Resekontroll, coacha din
> EuroBonus-status och utforska prisbelönta destinationer — med exakt de rättigheter du
> har på webben. Kräver ett ReseAssistenten-konto. Utgivare: Mindtravel.

Connect Claude to your own **ReseAssistenten** account to plan SAS award trips, run
Resekontroll (trip-readiness checks), coach your EuroBonus status, and explore
award-winning destinations — acting with exactly the permissions you have on the web.

## What it does & what data it sends

The plugin bundles **guided skills** plus a **connector** to ReseAssistenten's hosted,
per-user-authenticated MCP server at `https://reseassistenten.se/mcp` (declared in
`.mcp.json`, type `http`).

- On first use, your browser opens for **OAuth login + consent** on ReseAssistenten
  (dynamic client registration — **no tokens or secrets are stored in this plugin**).
- Once connected, the assistant reads (and, with the write permissions you grant, edits)
  **your own** trips, bookings, travel documents, award availability, EuroBonus status and
  destination catalogue — scoped to exactly what your ReseAssistenten web account can see.
- Data flows only between your Claude client and `https://reseassistenten.se`. The plugin
  itself ships no analytics, no third-party calls, and no bundled credentials.
- Read is available on the free tier; purchases are never available through the connector.

Privacy policy: https://reseassistenten.se/privacy · Terms: https://reseassistenten.se/terms

## Requirements

- A **ReseAssistenten account** (https://reseassistenten.se).
- Claude Code, or claude.ai / Cowork once the plugin is listed in the directory.

## Install (Claude Code)

```bash
claude plugin marketplace add ReseAassistenten/plugin
claude plugin install reseassistenten@mindtravel
```

On first run the connector opens ReseAssistenten's OAuth login in your browser.

**claude.ai / Cowork:** coming via Anthropic's plugin directory (link added once approved).

**ChatGPT / Codex users:** use the companion OpenAI/Codex plugin in
[`ReseAassistenten/chatgpt-plugin`](https://github.com/ReseAassistenten/chatgpt-plugin).

## Components

| Component | What it is | Claude Code | claude.ai / Cowork |
|---|---|---|---|
| **Connector** (`.mcp.json`) | Remote MCP server (`https://reseassistenten.se/mcp`, OAuth) | ✅ | ✅ |
| **Skills** (`skills/`) | Guided workflows that compose the MCP tools | ✅ | ✅ |
| Slash-commands | Shipped **server-side** as MCP prompts (`/award`, `/trip-check`, `/eurobonus`, `/watch`, `/trips`, `/explore`) — available in any MCP client | ✅ | ✅ |
| Hooks / agents | none | — | — |

### Skills

- **award-trip-planning** — search award availability, verify freshness, summarise bookable options with links.
- **resekontroll** — run the trip-readiness review + entry requirements into a prioritised action list.
- **eurobonus-coach** — EuroBonus level-point progress and a concrete plan to the next tier.
- **award-watch** — create/adjust award-availability watches for a route.
- **explore-destinations** — browse award-winning experiences by theme, or one city's guide.

## Publisher

**Mindtravel** · reseassistenten@mindtravel.se · https://mindtravel.se

## License

[MIT](./LICENSE).
