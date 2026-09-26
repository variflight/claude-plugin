# VariFlight plugin for Claude

Ask Claude about flights and get answers from VariFlight's live aviation data: flight status and delays, direct and connecting flights, airfare and itinerary summaries, flight comfort, three-day airport weather, and live aircraft positions.

## What's included

| Component | Purpose |
|---|---|
| `variflight-aviation` MCP server | Flight status, flight search, connecting flights, fares, itinerary summaries, flight comfort, airport weather, live aircraft position |
| `variflight-travel-lookup` skill | Tells Claude which tool fits each question, how to format dates and codes, and how to keep credit usage low |

## Setup

1. Create a VariFlight account at [ai.variflight.com](https://ai.variflight.com). New accounts include free credits; see the site for current pricing.
2. Add this plugin in Claude.
3. Connect VariFlight when Claude asks. In claude.ai and Cowork, open the plugin's **Connectors** tab and select **Connect**. In Claude Code, run `/mcp` and authenticate `variflight-aviation`. Sign-in uses OAuth on ai.variflight.com, so you never paste an API key into Claude.

## Example prompts

- "Is MU5100 on time today?"
- "Find flights from Beijing to Shanghai tomorrow morning."
- "What's the cheapest flight from Hefei to Guangzhou on 2026-10-01?"
- "How comfortable is CA1501, and what aircraft does it use?"
- "What's the weather at PVG for the next three days?"

## Data and privacy

- The plugin sends only the query parameters of each tool call (flight numbers, airport or city codes, dates, aircraft registrations) to VariFlight's servers at `https://ai.variflight.com`. It sends no other conversation content, and it runs no local code, hooks or scripts.
- Requests are tied to your VariFlight account through OAuth. Every tool except `getTodayDate` uses credits from that account.
- Privacy policy: [ai.variflight.com/privacy-policy](https://ai.variflight.com/privacy-policy). Terms of service: [ai.variflight.com/terms](https://ai.variflight.com/terms).

## Support

Manage your account, credits and connections at [ai.variflight.com](https://ai.variflight.com). For help, contact VariFlight through the site.

## License

[MIT](LICENSE)
