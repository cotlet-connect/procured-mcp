# Procured MCP server for ChatGPT and Claude

Procured states that it has no public API. Cotlet.dev connects ChatGPT, Claude and other AI agents to your signed-in Procured account with 12 hosted tools for quotes, invoices, crew scheduling, inventory and business reports.

## What you can ask

> Draft a quote with line items and a deposit for a new lead.

> Schedule a visit and dispatch it to a team member.

> Create an invoice for a finished job.

> Read the profit and loss report for this month.

> Read inventory and the materials used on a job.

> Review new client request form submissions.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Run the local MCP bridge

Python 3.10+, with no dependencies. Clone this repository, set your Cotlet.dev API key, then run:

```bash
export COTLET_API_KEY="your-key"
python3 procured_agent.py serve
```

This local stdio bridge lists seven browser helper tools: `procured_guide`, `procured_status`, `procured_open`, `procured_read`, `procured_click`, `procured_type` and `procured_close`.
It forwards calls to the hosted Cotlet.dev MCP server.
The 12 task tools described on the integration page are available through the hosted connection.

Without a key, the local bridge can list its helpers; calls return setup instructions.

```bash
python3 procured_agent.py connect
python3 procured_agent.py guide
python3 procured_agent.py status
```

## Questions from Procured users

**Does Procured have a public API or MCP server?**

The Cotlet.dev integration page, checked 17 Nov 2026, reports no public Procured API, MCP server or official ChatGPT or Claude connector.

**Does my Procured plan matter?**

The dispatch map and team chat need Procured Team or Business, as described on the integration page.

**Does Cotlet.dev take card payments?**

Clients pay Procured invoices through Stripe as before. The invoice tool can record a payment received outside Stripe after your approval.

**Is this an official Procured integration?**

No. Cotlet.dev is independent and is not affiliated with Procured.

## Integration details

[Procured tools and setup on Cotlet.dev](https://cotlet.dev/integrations/procured-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=procured)

---

More: https://cotlet.dev/integrations/procured-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=procured

Start free: https://cotlet.dev/signup?app=procured&utm_source=github&utm_medium=readme&utm_campaign=procured
