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

Find **Funnel** in the ChatGPT app directory and connect your Funnel account. See [Connect Funnel MCP to ChatGPT](https://help.funnel.io/en/articles/16522580).

### Claude

Open **Customize → Connectors**, find **Funnel** in the Connectors Directory, and connect your account. See [Connect Funnel MCP to Claude](https://help.funnel.io/en/articles/15170890).

### Claude Code

Add Funnel as a remote HTTP server. See [Connect Funnel MCP to Claude Code](https://help.funnel.io/en/articles/16526897).

```bash
claude mcp add --transport http funnel https://mcp.ai.funnel.io/mcp
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
| `list_guides` | List curated Funnel guides when guide_id is omitted. |
| `list_exports` | Lists the workspace's configured data exports and views. |
| `get_export` | Reads one export or view and returns its configuration and query template. |
| `list_export_connections` | Lists the user's own connections that can write to an export destination. |
| `list_export_destinations` | Lists where Funnel data can be exported and how each destination is set up. |
| `prepare_create_export` | Proposes a scheduled export to Google Sheets, BigQuery, Snowflake or Cloud Storage without creating it. |
| `prepare_set_export_enabled` | Proposes turning an export on or off without changing it. |
| `prepare_run_export` | Proposes running an export now without running it. |
| `execute_export_change` | Applies an approved export proposal exactly once. |
| `list_budgets` | Lists the workspace's configured Plan budgets. |
| `list_archived_budgets` | Lists the workspace's archived Plan budgets. |
| `get_budget` | Reads one Plan budget's configuration by ID. |
| `list_conventions` | Lists the workspace's active Plan Conventions. |
| `list_archived_conventions` | Lists the workspace's archived Plan Conventions. |
| `get_convention` | Reads one active Plan Convention's patterns and output fields by ID. |
| `prepare_update_budget` | Proposes a budget name or description change without writing it. |
| `prepare_archive_budget` | Proposes archiving one Plan budget without changing it yet. |
| `prepare_restore_budget` | Proposes restoring one archived Plan budget without changing it yet. |
| `execute_budget_change` | Applies an approved budget proposal exactly once. |
| `get_flexpoint_usage` | Reads the Flexpoints the workspace's subscription has used and has left. |
| `get_flexpoint_usage_by_workspace` | Reads the subscription's Flexpoints per workspace. |
| `get_flexpoint_usage_by_connector` | Reads the subscription's Flexpoints per connector and destination type. |
| `list_portals` | Lists the workspace's client portals with their brand, dashboard count and user count. |
| `get_portal` | Reads one client portal of the workspace by ID. |
| `list_portal_dashboards` | Lists the dashboards in one client portal. |
| `get_portal_dashboard_groups` | Reads how a portal's dashboards are grouped and ordered for its viewers. |
| `list_portal_users` | Lists the users who can open one client portal. |
| `list_dashboards` | Lists the workspace's dashboards by title, with their IDs. |
| `check_portal_dashboards` | Checks which dashboards could be added to a portal, without changing it. |
| `list_brands` | Lists the portal brands of the workspace's subscription. |
| `prepare_create_portal` | Proposes a new client portal without creating it yet. |
| `prepare_update_portal` | Proposes a client portal rename, description or brand change without writing it. |
| `prepare_delete_portal` | Proposes deleting one client portal without changing it yet. |
| `prepare_add_dashboards_to_portal` | Proposes adding dashboards to a client portal without changing it yet. |
| `prepare_remove_dashboards_from_portal` | Proposes removing dashboards from a client portal without changing it yet. |
| `prepare_set_portal_dashboard_groups` | Proposes how a portal's dashboards are grouped and ordered, without writing it. |
| `execute_portal_change` | Applies an approved client portal proposal exactly once. |
| `prepare_create_brand` | Proposes a new portal brand without creating it yet. |
| `prepare_update_brand` | Proposes a portal brand name or colour change without writing it. |
| `prepare_delete_brand` | Proposes deleting one portal brand without changing it yet. |
| `execute_brand_change` | Applies an approved portal brand proposal exactly once. |
| `list_connectors` | Lists connectors available for data-source setup in the workspace. |
| `list_connector_templates` | Lists curated template candidates for a connector. |
| `start_data_source_setup` | Starts guided data-source setup with the selected connector. |
| `select_data_source_connection` | Selects a connection for an in-progress data-source setup. |
| `select_data_source_remote_account` | Selects a remote account for an in-progress data-source setup. |
| `start_data_source_authentication` | Returns the browser sign-in link for a connector. |
| `list_data_source_templates` | Lists curated templates for the selected remote account. |
| `select_data_source_template` | Selects a curated template for an in-progress data-source setup. |
| `prepare_create_data_source` | Prepares a data-source creation proposal for user approval. |
| `execute_create_data_source` | Creates a Data Source from an approved proposal. |
| `mutate_fields` | Prepares custom field changes for user approval without writing anything. |
| `apply_field_mutation` | Applies approved custom field changes from a prepared plan. |
| `list_data_sources` | Lists active Data Sources in the workspace by name or connector, for inspection and management. |
| `list_deleted_data_sources` | Lists soft-deleted Data Sources in the workspace for inspection and restoration. |
| `inspect_data_source` | Reads the management state of one Data Source without changing it. |
| `rename_data_source` | Renames one Data Source after explicit user approval. |
| `set_data_source_downloads_enabled` | Enables or disables future downloads for a Data Source after explicit user approval. |
| `set_data_source_use_in_funnel` | Includes or excludes a Data Source from Funnel reporting after explicit user approval. |
| `reconnect_data_source` | Reconnects a Data Source to another connection after explicit user approval. |
| `reconfigure_data_source` | Changes a Data Source's curated template after explicit user approval. |
| `delete_data_source` | Soft-deletes a Data Source after explicit user approval. |
| `restore_data_source` | Restores a soft-deleted Data Source after explicit user approval. |

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
