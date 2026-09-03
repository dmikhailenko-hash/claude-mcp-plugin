# Trade Revolution MCP Plugin for Claude Code

A powerful Model Context Protocol (MCP) plugin that integrates Trade Revolution trading platform with Claude Code, enabling seamless access to trading tools, position management, and market data.

## Features

- **Order Management**: Place market, limit, stop, and trailing stop orders
- **Position Management**: View, modify, and close trading positions
- **Account Management**: Monitor account state, balance, margin, and P&L
- **Market Data**: Access real-time quotes, price bars, and order book depth
- **Risk Management**: Configure stop loss and take profit levels
- **Trading History**: View trades, executions, and account statements
- **Multi-Account Support**: Manage multiple trading accounts

## Installation

### Prerequisites
- Claude Code (latest version)
- Active Trade Revolution trading account with API access

### Setup

1. **Add to Claude Code Configuration**

Add the following to your `.claude/mcp.json`:

```json
{
  "mcpServers": {
    "traderevolution": {
      "url": "https://test-clientapi.traderevolution.com/traderevolution/v1/mcp"
    }
  }
}
```

2. **Restart Claude Code** to activate the plugin

3. **Start Using** - The Trade Revolution MCP tools will now be available in Claude Code

## Available Tools

### Account Tools
- `get_accounts` - List all trading accounts
- `get_account_state` - Get comprehensive account balance and P&L
- `get_config` - View account configuration

### Order Management
- `place_order` - Place a new trading order
- `get_orders` - View pending orders
- `modify_order` - Update order parameters
- `cancel_order` - Cancel a pending order
- `cancel_all_orders` - Cancel all pending orders
- `get_orders_history` - View order history

### Position Management
- `get_positions` - View all open positions
- `modify_position` - Update position SL/TP levels
- `close_position` - Close a specific position
- `close_all_positions` - Close all open positions

### Market Data
- `get_instruments` - Search tradable instruments
- `get_quotes` - Get real-time price quotes
- `get_last_bar` - Get latest price bar
- `get_daily_bar` - Get daily OHLC data
- `get_depth` - View order book depth

### Trading Activity
- `get_trades` - View executed trades
- `get_executions` - View order executions
- `get_statement` - Get account statement
- `get_history` - View account history

### Risk Management
- `risk_details` - Get risk information
- `get_risk_rules_counters` - View risk rule status

## Usage Examples

### Check Account Status
```
User: Show my account state
Claude: [retrieves account balance, P&L, margin info]
```

### Place an Order
```
User: Buy 1 GOOG at market, DAY validity
Claude: [places order and confirms execution]
```

### View Positions
```
User: Show my open positions
Claude: [displays all open positions with P&L]
```

## Security

- No hardcoded credentials required
- All authentication handled through Trade Revolution API
- Secure connection via HTTPS
- Support for API key management

## Support

For issues, feature requests, or questions:
- GitHub Issues: [Project Repository]
- Trade Revolution Support: https://traderevolution.com

## License

MIT License - See LICENSE file for details

## Version History

### v1.0.0 (2026-09-03)
- Initial release
- Full support for order, position, and account management
- Real-time market data access
- Risk management tools
