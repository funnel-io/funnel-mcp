# Funnel MCP

Connect your AI agent to your Funnel marketing data. Ask cross-channel performance questions, track pacing against budgets and targets, and drill into campaigns, creatives, and keywords directly from Claude, Cursor, Codex, Gemini CLI, or any MCP-compatible client.

With the Funnel MCP server, you can:

- **Compare performance across channels** with consistent metrics across Google Ads, Facebook Ads (Meta), TikTok Ads, LinkedIn Ads, Google Analytics, Microsoft Advertising (Bing Ads), Shopify, HubSpot, and 600+ other platforms.
- **Track pacing** against budgets and revenue targets.
- **Drill into campaigns, ads, creatives, and keywords** to find what's driving performance.
- **Explore your own semantics and business context**, not just raw platform data.

## Server URLs

| Region | URL |
|--------|-----|
| Global (default) | `https://mcp.ai.funnel.io/mcp` |
| EU (data residency) | `https://mcp.eu.ai.funnel.io/mcp` |

## Installation

### Claude (claude.ai, Claude Desktop)

Add as a custom connector under **Settings → Connectors**. Use the Global or EU URL from the table above.

### Claude Code

```
/plugin install funnel-io/funnel-mcp
```

### Cursor

Install from the [Cursor Marketplace](https://cursor.com/marketplace), or add manually in **Settings → MCP**:

```json
{
  "mcpServers": {
    "funnel": {
      "url": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

### Codex

```
/plugins add funnel-io/funnel-mcp
```

### Gemini CLI

```
gemini extensions install https://github.com/funnel-io/funnel-mcp
```

### Google Antigravity

Open **Manage MCP Servers → View raw config** to edit `mcp_config.json`, then add:

```json
{
  "mcpServers": {
    "funnel": {
      "serverUrl": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

Antigravity uses `serverUrl` (not `url`) for remote MCP servers.

### VS Code (Copilot agent mode), Windsurf, Zed, Continue, or any other MCP client

Add to your client's MCP config:

```json
{
  "mcpServers": {
    "funnel": {
      "url": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

EU customers: replace the URL with `https://mcp.eu.ai.funnel.io/mcp`.

For a full list of supported MCP clients, see the [Funnel MCP docs](https://help.funnel.io/en/articles/15014203-quick-start-guide-using-funnel-mcp).

## Authentication

Funnel uses OAuth 2.0. Your MCP client will send you to funnel.io to sign in on first use. Requires access to a Funnel workspace.

## Available tools

| Tool | Description |
|------|-------------|
| `list_workspaces` | Lists Funnel workspaces accessible to the current user. |
| `load_workspace` | Loads a workspace's available data: ad platforms, dimensions (campaign name, country, ad group, etc.), measures (spend, clicks, impressions), and metrics (CPC, CTR, ROAS, etc.). |
| `get_workspace_context` | Retrieves workspace context — administrator-defined conventions, business rules, and domain terminology — so analysis aligns with how your team works. Call once per workspace after load_workspace. |
| `search_fields` | Finds available dimensions, measures, and metrics in a workspace. |
| `get_dimension_values` | Returns actual values for a dimension field within a date range — e.g., campaign names, country codes, ad group names, platform names. |
| `query_data` | Queries advertising data from connected platforms. |
| `prepare_data` | Loads raw, row-level data without aggregation — every individual data point as reported by the ad platform. |

## Resources

- [Funnel docs](https://help.funnel.io/en/)
- [Quick start guide](https://help.funnel.io/en/articles/15014203-quick-start-guide-using-funnel-mcp)
- [MCP Protocol](https://modelcontextprotocol.io/)

## License

MIT

## Support

- **Issues**: [GitHub Issues](https://github.com/funnel-io/funnel-mcp/issues)
- **Help center**: [help.funnel.io](https://help.funnel.io/)
- **Privacy**: [funnel.io/funnel-data-privacy-and-security](https://funnel.io/funnel-data-privacy-and-security)
- **Terms**: [funnel.io/general-terms-and-conditions](https://funnel.io/general-terms-and-conditions)
