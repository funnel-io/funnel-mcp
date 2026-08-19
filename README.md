# Funnel MCP

Connect your AI agent to Funnel marketing data. Compare cross-channel performance, track pacing against budgets and targets, and analyze campaigns directly from your MCP-compatible client.

With the Funnel MCP server, you can:

- **Compare performance across channels** using consistent metrics from 600+ marketing and sales platforms.
- **Track pacing** against budgets and revenue targets.
- **Drill into campaigns, ads, creatives, and keywords** to understand performance drivers.
- **Use your Funnel semantics and business context** instead of relying only on raw platform data.

## Server URLs

| Region | URL |
|--------|-----|
| Global (default) | `https://mcp.ai.funnel.io/mcp` |
| EU data residency | `https://mcp.eu.ai.funnel.io/mcp` |

All repository and catalog manifests use the global endpoint. If your Funnel workspace requires EU data residency, use the EU URL in manual client configurations.

## Installation

### ChatGPT

Find **Funnel** in the ChatGPT app directory and connect your Funnel account.

### Claude

In Claude.ai or Claude Desktop, open **Settings → Connectors**, choose **Add custom connector**, and enter the server URL for your region.

### Claude Code

Add this repository as a marketplace and install the Funnel plugin:

```text
/plugin marketplace add funnel-io/funnel-mcp
/plugin install funnel@funnel
```

### Cursor

Open **Settings → MCP** and add:

```json
{
  "mcpServers": {
    "funnel": {
      "url": "https://mcp.ai.funnel.io/mcp",
      "auth": {
        "CLIENT_ID": "4HiYmsg53mSStXa3UqfStADOhZ1tF6Y0"
      }
    }
  }
}
```

### Codex

Add the Funnel marketplace:

```text
codex plugin marketplace add funnel-io/funnel-mcp
```

Then run `/plugins` in Codex and install `funnel`.

### Antigravity CLI

Install the repository as a native Antigravity plugin:

```text
agy plugin install https://github.com/funnel-io/funnel-mcp
```

Then run `/mcp` in Antigravity CLI to authenticate and inspect the Funnel server.

### Google Antigravity IDE

Open **Manage MCP Servers → View raw config** and add:

```json
{
  "mcpServers": {
    "funnel": {
      "serverUrl": "https://mcp.ai.funnel.io/mcp",
      "oauth": {
        "clientId": "4HiYmsg53mSStXa3UqfStADOhZ1tF6Y0"
      }
    }
  }
}
```

Antigravity uses `serverUrl` for remote MCP servers.

### VS Code (Copilot agent mode)

Add the server to VS Code's top-level `servers` configuration:

```json
{
  "servers": {
    "funnel": {
      "type": "http",
      "url": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

### Windsurf

Add the server using Windsurf's `mcpServers` and `serverUrl` keys:

```json
{
  "mcpServers": {
    "funnel": {
      "serverUrl": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

### Zed

Add the server to Zed's `context_servers` settings:

```json
{
  "context_servers": {
    "funnel": {
      "url": "https://mcp.ai.funnel.io/mcp"
    }
  }
}
```

### Continue

Add a Streamable HTTP server to Continue's YAML configuration:

```yaml
mcpServers:
  - name: funnel
    type: streamable-http
    url: https://mcp.ai.funnel.io/mcp
```

For any manual configuration above, replace `https://mcp.ai.funnel.io/mcp` with `https://mcp.eu.ai.funnel.io/mcp` when using Funnel's EU data-residency endpoint.

## Authentication

Funnel uses OAuth 2.0. Your MCP client sends you to Funnel to sign in on first use. You need access to a Funnel workspace.

## Available tools

| Tool | Description |
|------|-------------|
| `list_workspaces` | Lists Funnel workspaces accessible to the current user, grouped by subscription. |
| `load_workspace` | Loads a workspace's available data: ad platforms, dimensions (campaign name, country, ad group, etc.), measures (spend, clicks, impressions), and metrics (CPC, CTR, ROAS, etc.). |
| `get_workspace_context` | Retrieves workspace context — administrator-authored conventions, business rules, and domain terminology — to improve analysis accuracy and terminology alignment. |
| `search_fields` | Finds dimensions, measures, metrics, and connected Data Sources in a workspace. |
| `get_dimension_values` | Returns actual values for a dimension field within a date range. |
| `query_data` | Queries advertising data and stores named session tables for follow-up analysis. |
| `prepare_data` | Loads raw, row-level data without aggregation for custom analysis and re-slicing. |

## Resources

- [Funnel documentation](https://help.funnel.io/en/)
- [Funnel MCP quick start](https://help.funnel.io/en/articles/15014203-quick-start-guide-using-funnel-mcp)
- [Model Context Protocol](https://modelcontextprotocol.io/)

## License

This repository is available under the [MIT License](LICENSE).

## Security

See [SECURITY.md](SECURITY.md) and [Funnel data privacy and security](https://funnel.io/funnel-data-privacy-and-security).

## Support

- **Issues**: [GitHub Issues](https://github.com/funnel-io/funnel-mcp/issues)
- **Help center**: [help.funnel.io](https://help.funnel.io/)
- **Privacy**: [Funnel data privacy and security](https://funnel.io/funnel-data-privacy-and-security)
- **Terms**: [Funnel terms and conditions](https://funnel.io/general-terms-and-conditions)
