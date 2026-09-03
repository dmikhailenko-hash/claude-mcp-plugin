# Trade Revolution MCP Plugin Setup Guide

Complete step-by-step guide to set up and use the Trade Revolution MCP plugin in Claude Code.

## Prerequisites

- Claude Code installed and updated to latest version
- Active Trade Revolution trading account
- Your Trade Revolution username and password

## Installation

### Step 1: Install the Plugin

The Trade Revolution MCP plugin comes with built-in OAuth authentication. No manual credential setup is required!

### Step 2: First Use Setup

1. Open Claude Code
2. Try a Trading Revolution command, for example:
   ```
   Show my account balance
   ```

3. Claude Code will prompt you to authenticate:
   - A login page will open
   - Enter your Trade Revolution **username**
   - Enter your Trade Revolution **password**
   - Click **Login**

4. Grant Permission:
   - Claude Code will ask for permission to access your account
   - Click **Approve** or **Grant Access**

5. You're Connected!
   - You'll be redirected back to Claude Code
   - All Trade Revolution tools are now available
   - Start using trading features!

### Step 3: Verify Installation

Once authenticated, try these commands:

```
User: Get my accounts
Claude: [displays your trading accounts]

User: Show my positions  
Claude: [displays your open positions]

User: What's my account balance?
Claude: [shows account state and balance]
```

## How It Works

The plugin uses a secure OAuth 2.0 authentication flow:

```
1. You run a Trading Revolution command in Claude Code
   ↓
2. Claude Code connects to Trade Revolution OAuth
   ↓
3. You're redirected to Trade Revolution login page
   ↓
4. You enter your username and password
   ↓
5. You approve Claude Code access
   ↓
6. Secure session token is created
   ↓
7. You return to Claude Code with active session
   ↓
8. All commands use your authenticated session
```

## Features & Commands

Once authenticated, you can:

### View Account Information
- `Get my account state` - Balance, margin, P&L
- `Get my accounts` - List all trading accounts
- `Show my account balance` - Current balance

### Manage Positions
- `Show my positions` - View open positions
- `Close position [ID]` - Close a specific position
- `Modify position [ID]` - Update stop loss/take profit

### Trading Orders
- `Buy 1 AAPL at market` - Place market order
- `Buy 10 shares at limit 150` - Place limit order
- `Get my orders` - View pending orders
- `Cancel order [ID]` - Cancel an order

### Market Data
- `Get GOOG price` - Real-time quotes
- `Show AAPL daily bars` - Price history
- `Get market depth` - Order book info

## Troubleshooting

### "Cannot authenticate" or "Login failed"
- ✅ Check your Trade Revolution username and password
- ✅ Make sure your account is active
- ✅ Try logging in directly to Trade Revolution website
- ✅ Restart Claude Code and try again

### "Permission denied" after login
- ✅ You need to approve access in the OAuth consent screen
- ✅ Try logging in again and click "Approve"

### "Session expired"
- ✅ Log out and log in again
- ✅ Some sessions expire after inactivity - re-authenticate
- ✅ Restart Claude Code

### "MCP not found" or "Cannot connect"
- ✅ Check internet connection
- ✅ Make sure Claude Code is updated
- ✅ Restart Claude Code completely
- ✅ Check if Trade Revolution service is available

### No trading tools showing up
- ✅ Make sure you're authenticated (see First Use Setup)
- ✅ Restart Claude Code
- ✅ Clear Claude Code cache: Settings → Clear Cache

## Troubleshooting

### "Connection refused" or "Cannot connect to MCP"
- ✅ Check if `.claude/mcp.json` is saved correctly
- ✅ Verify OAuth Client ID and Secret are correct
- ✅ Restart Claude Code
- ✅ Check internet connection

### "Invalid credentials" or "Unauthorized"
- ✅ Verify Client ID and Secret spelling (case-sensitive)
- ✅ Make sure you copied the entire secret
- ✅ OAuth credentials may be expired - regenerate new ones

### "URL not found" error
- ✅ Check the MCP URL is correct: `https://test-clientapi.traderevolution.com/traderevolution/v1/mcp`
- ✅ Verify your Trade Revolution account has API access enabled

### No tools are appearing
- ✅ Fully close and restart Claude Code
- ✅ Clear Claude Code cache (Settings → Clear Cache)
- ✅ Reinstall the plugin

## Security Best Practices

⚠️ **Important Security Notes:**

1. **Never Share Your Secret**
   - OAuth Client Secret is like a password
   - Never post it online, in GitHub, or share with anyone
   - If compromised, regenerate immediately

2. **Keep mcp.json Private**
   - Don't add it to git version control
   - Add `.claude/` to your `.gitignore` if you have one
   - Only store on your personal machine

3. **Rotate Credentials**
   - If you suspect compromise, regenerate credentials
   - Delete the old ones from Trade Revolution settings
   - Update your `.claude/mcp.json`

4. **Use Environment Variables (Optional)**
   - For added security, you can use environment variables:
   ```json
   {
     "mcpServers": {
       "traderevolution": {
         "url": "https://test-clientapi.traderevolution.com/traderevolution/v1/mcp?client_id=${TRADE_REVOLUTION_CLIENT_ID}&client_secret=${TRADE_REVOLUTION_CLIENT_SECRET}"
       }
     }
   }
   ```
   - Set environment variables:
     - Windows: `set TRADE_REVOLUTION_CLIENT_ID=your_id`
     - Mac/Linux: `export TRADE_REVOLUTION_CLIENT_ID=your_id`

## Advanced Configuration

### Multiple Accounts

If you have multiple Trade Revolution accounts, you can configure them separately:

```json
{
  "mcpServers": {
    "traderevolution-main": {
      "url": "https://test-clientapi.traderevolution.com/traderevolution/v1/mcp?client_id=ACCOUNT1_ID&client_secret=ACCOUNT1_SECRET"
    },
    "traderevolution-secondary": {
      "url": "https://test-clientapi.traderevolution.com/traderevolution/v1/mcp?client_id=ACCOUNT2_ID&client_secret=ACCOUNT2_SECRET"
    }
  }
}
```

## Support

For issues or questions:
- Check this setup guide first
- Review Trade Revolution documentation
- Check Claude Code logs for errors
- Contact Trade Revolution support

## Uninstallation

To remove the plugin:
1. Open `.claude/mcp.json`
2. Remove the `traderevolution` entry from `mcpServers`
3. Save and restart Claude Code

The plugin will no longer be available.
