# Trade Revolution — Claude Code Plugin

A Claude Code plugin that bundles the TraderEvolution MCP server, giving Claude access to trading
operations on your TraderEvolution account: orders, positions, account state, and market data.

## What's inside

This plugin ships a single remote MCP server (`traderevolution`) over streamable HTTP. Installing the
plugin registers that server — there is no manual MCP configuration to write.

```
.claude-plugin/plugin.json   plugin manifest
.mcp.json                    bundled MCP server definition
```

## Requirements

- Claude Code
- An active TraderEvolution account

## Installation

### From a marketplace

```
/plugin marketplace add dmikhailenko-hash/claude-mcp-plugin
/plugin install trade-revolution@claude-mcp-plugin
```

### For local development

Clone the repository and start Claude Code with the plugin loaded directly:

```
git clone https://github.com/dmikhailenko-hash/claude-mcp-plugin.git
claude --plugin-dir ./claude-mcp-plugin
```

Verify the plugin loaded with `/plugin` (check the **Errors** tab if it doesn't appear) and check the
MCP server's connection state with `/mcp`.

## Authentication

The MCP server authenticates each user through TraderEvolution's OAuth flow. On first use you are
directed to the TraderEvolution sign-in page, where you log in with **your own** username and
password and approve access. Each user operates against their own account and their own session.

No credentials are stored in this repository, and none need to be added to your Claude Code
configuration.

## Available tools

**Accounts** — `get_accounts`, `get_account_state`, `get_config`

**Orders** — `place_order`, `modify_order`, `cancel_order`, `cancel_all_orders`, `get_orders`,
`get_orders_history`

**Positions** — `get_positions`, `modify_position`, `close_position`, `close_all_positions`

**Market data** — `get_instruments`, `get_instrument_details`, `get_quotes`, `get_last_bar`,
`get_daily_bar`, `get_depth`

**Activity** — `get_trades`, `get_executions`, `get_statement`, `get_history`

**Risk** — `risk_details`, `get_risk_rules_counters`

## Notes

Visiting the MCP endpoint directly in a browser returns
`Invalid Accept header. Expected TEXT_EVENT_STREAM`. This is correct behaviour — the endpoint requires
`Accept: text/event-stream`, which a browser does not send and an MCP client does. It is not an error
condition.

The server URL currently points at a test environment.

## License

MIT — see [LICENSE](LICENSE).
