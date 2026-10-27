<p align="center"><img src="logo.png" width="96" alt="Stay Cost Brain"></p>

# Stay Cost Brain MCP server

**Tourist and hotel taxes, for AI assistants.** What a stay really adds on top of the room price: the tourist, city,
occupancy or hotel tax, taken from each tax authority's own pages, regulations or official gazette, with the source
and the date it was checked, and worked out night by night for the dates and guests.

Free. No API key. No login. Read-only.

**MCP endpoint (streamable HTTP):**

```
https://staycostbrain.com/mcp
```

Website: [staycostbrain.com](https://staycostbrain.com) · Full data summary for AI readers:
[llms-full.txt](https://staycostbrain.com/llms-full.txt)

## Why it exists

Booking sites show the room price. The tax on top is often charged at the hotel, differs by star rating, season and
age, and in many places is stacked from state, regional and city parts. Stay Cost Brain keeps sourced, dated tables
for 71 places in 18 countries (including 27 in the US) and answers with the amounts, so an assistant can say
what a stay will really cost.

## Tools

| Tool | What it answers |
|---|---|
| `get_capabilities` | What is covered, how figures are sourced and dated, what it does not do |
| `list_places` | Every researched place: headline rate, check date, re-check date, towns with their own tax |
| `tourist_tax` | The tax for one stay, night by night: each tax separately, amount or range, nights charged, how it is paid, announced changes, source and date |
| `place_rules` | Every rule for one place: rates by type of stay, seasons, caps, exemptions, status, sources |
| `hotels_link` | A link to live hotel and rental prices for the dates and guests, where the person books (Stay22; Stay Cost Brain may earn a commission) |

Towns that haven't been researched return `researched: false` and no figure: nothing is estimated and presented as fact.

## Example questions

- "How much hotel tax will I pay in New York City for 2 nights if the room costs $600 in total?"
- "What is the tourist tax for 3 nights in a 4-star hotel in Barcelona for 2 adults?"
- "Do children pay the tourist tax in Lisbon?"
- "Who is exempt from the tourist tax in Venice?"
- "Find hotels in Lisbon for 20 to 23 November for 2 adults."

## Connect

<details>
<summary><strong>Claude Code (this repository is a plugin)</strong></summary>

```
/plugin marketplace add jimiwalters-cmyk/stay-cost-brain-mcp
/plugin install stay-cost-brain@stay-cost-brain
```

Or add the server directly:

```
claude mcp add --transport http stay-cost-brain https://staycostbrain.com/mcp
```
</details>

<details>
<summary><strong>Claude (claude.ai / Claude Desktop)</strong></summary>

Find **Stay Cost Brain** in the connectors directory, or Customize → Connectors → Add custom connector → URL
`https://staycostbrain.com/mcp`, no authentication.
</details>

<details>
<summary><strong>Any other MCP client</strong></summary>

```json
{
  "mcpServers": {
    "stay-cost-brain": { "type": "http", "url": "https://staycostbrain.com/mcp" }
  }
}
```
</details>

The same answers are available as plain JSON at `https://staycostbrain.com/api/v1/<tool>`.

## Data and privacy

No account, nothing personal requested. The server receives only the tool arguments (place, dates, party size, room
price). Privacy: [staycostbrain.com/privacy](https://staycostbrain.com/privacy/) · Terms:
[staycostbrain.com/terms](https://staycostbrain.com/terms/) · Support: hello@staycostbrain.com

Rate limit: 30 requests per 10 seconds per IP.

## Licence

The files in this repository are Apache-2.0 (see [LICENSE](LICENSE) and [NOTICE](NOTICE)). The Stay Cost Brain name,
logo, server, code and data are not covered.

Part of the Brain family: [Car Rental Brain](https://github.com/jimiwalters-cmyk/car-rental-brain-mcp) (car hire) and
Airfare Brain (flight extras).
