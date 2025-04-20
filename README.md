# Telegram WEB Socket Server 

## Overview

MCP (Message Control Protocol) Telegram Bot is a powerful tool for accessing Telegram channel messages via WebSocket connection. The bot allows you to receive messages from your channels in real-time and create your own integrations.
 - 👉 Try it now:WEB Socket Server https://t.me/MCPServer_bot

## Key Features

- 🔌 **WebSocket API** for receiving messages in real-time
- 🔐 **Token system** for secure API access
- 📱 **Media content support** (photos, videos, documents, audio)
- 🌐 **Multilingual support** (Russian, English)
- 👥 **Connection limits** based on subscription plan
- 📝 **Message history storage**

## Getting Started

1. Add the bot to your Telegram channel as an administrator
2. Use the `/start` command in a private chat with the bot
3. Add your channel through the bot menu
4. Get an access token for the MCP API
5. Connect to the API via WebSocket to receive messages

## Subscription Plans

The bot offers several subscription plans:

| Plan    | Price     | Duration    | Channel Limit | Connections |
|---------|-----------|-------------|---------------|-------------|
| Free    | Free      | 7 days      | 3             | 1           |
| Basic   | $15       | 30 days     | 10            | 3           |
| Pro     | $39       | 90 days     | 50            | 10          |
| Premium | $99       | 365 days    | 1000          | 50          |

## Payment Methods

The following payment methods are supported:
- 💎 **TON** (The Open Network) - Telegram's native cryptocurrency

## Architecture

The bot is built on a modern technology stack:

- **Python** - primary programming language
- **Telethon** - library for working with Telegram API
- **python-telegram-bot** - for handling commands via Bot API
- **MongoDB** - for storing user, channel, and message data
- **WebSockets** - for implementing the MCP protocol
- **aiohttp** - for web server and HTTP requests

## Using the MCP API

The MCP API allows you to receive messages from Telegram channels in real-time via WebSocket connection.

### Connection

```javascript
// JavaScript connection example
const ws = new WebSocket('wss://your-server/ws');

// Send token for authentication
ws.onopen = () => {
  ws.send(JSON.stringify({ token: 'your_token_here' }));
};

// Handle messages
ws.onmessage = (event) => {
  const data = JSON.parse(event.data);
  
  if (data.type === 'connected') {
    console.log('Successfully connected to MCP server');
    
    // Subscribe to a channel
    ws.send(JSON.stringify({
      type: 'subscribe',
      channel_id: '@channel_name'
    }));
  }
  else if (data.type === 'new_message') {
    console.log('New message received:', data.message);
  }
};
```

### Available Commands

- `subscribe` - subscribe to a channel
- `unsubscribe` - unsubscribe from a channel
- `get_history` - retrieve message history
- `get_channels` - get list of available channels
- `ping` - check connection

## Security

- 🔒 All API connections are protected by tokens
- ⏱️ Tokens have a limited validity period
- 🛡️ User access to channels is verified
- 📊 Monitoring and limiting the number of connections

## Benefits

- Ease of use - simply add the bot to your channel and get a token
- No additional API keys or settings required from the user
- Low latency when receiving new messages
- Support for all types of Telegram media content
- Ability to retrieve channel message history

## License

Commercial use. Contact for licensing.

---

© 2025 MCP Telegram Bot
