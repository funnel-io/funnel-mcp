# Funnel Analytics MCP Server

> **This repository is auto-generated.** All changes must be made in [funnel-io/conversational-analytics](https://github.com/funnel-io/conversational-analytics) under `funnel-mcp/public-listing/`.

Connect your AI agent to Funnel marketing data — query ad pipelines, explore connected platforms and fields, and analyze spend directly from your terminal or chat interface.

## Quick start

Add this to your `.mcp.json` (or your AI client's MCP server config):

```json
{
  "mcpServers": {
    "funnel": {
      "url": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

> **EU customers:** replace the URL with `https://mcp.eu.ai.funnel.io/mcp` to keep your data within the EU.

## Available tools

| Tool | Description |
|------|-------------|
| `list_workspaces` | Lists Funnel workspaces accessible to the current user. |
| `load_workspace` | Loads a workspace's available data: ad platforms, dimensions (campaign name, country, ad group, etc.), measures (spend, clicks, impressions), and metrics (CPC, CTR, ROAS, etc.). |
| `search_fields` | Finds available dimensions, measures, and metrics in a workspace. |
| `get_dimension_values` | Returns actual values for a dimension field within a date range — e.g., campaign names, country codes, ad group names, platform names. |
| `query_data` | Queries advertising data from connected platforms. |
| `prepare_data` | Loads raw, row-level data without aggregation — every individual data point as reported by the ad platform. |

## Authentication

Funnel uses OAuth 2.0. Your MCP client will prompt you to sign in with your Funnel account on first use.

## Links

- [Homepage](https://funnel.io)
- [Terms of Service](https://funnel.io/general-terms-and-conditions)
- [Privacy Policy](https://funnel.io/funnel-data-privacy-and-security)
