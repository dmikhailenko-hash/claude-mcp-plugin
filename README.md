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
- Active Trade Revolution trading account with login credentials

### Quick Setup

The plugin uses Trade Revolution's OAuth authentication. Here's how it works:

1. **Install the plugin in Claude Code**
2. **First time you use it**, Claude Code will redirect you to Trade Revolution login page
3. **Log in with your username and password**
4. **Grant permission** for Claude Code to access your account
5. **Start trading!** You're now connected to your Trade Revolution account

### Detailed Setup

#### Option 1: Automatic Configuration (Recommended)

1. Open Claude Code
2. The MCP configuration will be auto-detected
3. On first use, you'll be prompted to authenticate
4. Follow the OAuth flow to log in to your Trade Revolution account

#### Option 2: Manual Configuration

1. Open your Claude Code configuration file `.claude/mcp.json`
2. Add the Trade Revolution MCP server:

```json
{
  "mcpServers": {
    "traderevolution": {
      "url": "https://test-clientapi.traderevolution.com/traderevolution/v1/mcp"
    }
  }
}
```

3. Save and restart Claude Code
4. On first use, you'll be prompted to authenticate via OAuth

### Authentication Flow

- The plugin uses **OAuth 2.0** for secure authentication
- You log in with your **personal Trade Revolution credentials**
- Each user has **their own session** and **separate account access**
- No passwords are stored in Claude Code
- Your session is maintained securely

### First Use

When you first use a Trade Revolution command in Claude Code:

1. Claude Code detects you're not authenticated
2. Directs you to Trade Revolution login page
3. Enter your **username** and **password**
4. Approve Claude Code access to your account
5. You're redirected back to Claude Code
6. Start using all Trading Revolution features!

### Logging Out / Resetting Authentication

To reset authentication or log out:

1. Remove the Trade Revolution credentials from your Claude Code session
2. Clear browser cookies from Trade Revolution (if using OAuth page)
3. Next time you use a command, you'll be prompted to log in again

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
