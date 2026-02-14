# AgentPMT MCP Server

AgentPMT is an AI agent marketplace for creating automated employees and assistants. This MCP server connects your AI agents to the AgentPMT ecosystem, enabling them to discover, purchase, and orchestrate tools, workflows, and skills.

## Features

- **Automated Employees & Assistants** - Build AI agents that work autonomously around the clock
- **Dynamic Tool Discovery** - Agents browse and discover tools from the marketplace in real-time
- **Autonomous Purchasing** - Agents can purchase and use tools with budget-controlled spending
- **Workflow Orchestration** - Chain multiple tools together into complex workflows
- **Enterprise Budget Controls** - Set spending limits, approve purchases, and monitor usage
- **Web3 Payments** - USDC payments on Base network for transparent, autonomous transactions

## Quick Start

### Connect via MCP

**Endpoint:** `https://api.agentpmt.com/mcp`
**Transport:** Streamable HTTP
**Protocol Version:** 2025-03-26

### Authentication

AgentPMT uses API key + budget key authentication. You need:

1. An **API Key** - identifies your account
2. A **Budget Key** - identifies which budget to charge

Get your keys at [agentpmt.com](https://agentpmt.com) by creating an account and setting up a budget.

### Configuration

#### Claude Desktop / Claude Code

Add to your MCP configuration:

```json
{
  "mcpServers": {
    "agentpmt": {
      "type": "streamable-http",
      "url": "https://api.agentpmt.com/mcp",
      "headers": {
        "Authorization": "Bearer <base64-encoded-credentials>"
      }
    }
  }
}
```

#### VS Code / GitHub Copilot

AgentPMT is available in the MCP server gallery. Search for `com.agentpmt/agentpmt` in the Extensions view (`@mcp` filter).

Or add manually to `.vscode/mcp.json`:

```json
{
  "servers": {
    "agentpmt": {
      "type": "streamable-http",
      "url": "https://api.agentpmt.com/mcp",
      "headers": {
        "Authorization": "Bearer <base64-encoded-credentials>"
      }
    }
  }
}
```

#### <a id="cursor"></a>Cursor

**One-click install:** [Install AgentPMT in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=agentpmt&config=eyJ1cmwiOiAiaHR0cHM6Ly9hcGkuYWdlbnRwbXQuY29tL21jcCIsICJoZWFkZXJzIjogeyJBdXRob3JpemF0aW9uIjogIkJlYXJlciBZT1VSX0FQSV9LRVkifX0%3D)

Or add manually to your Cursor MCP settings:

```json
{
  "mcpServers": {
    "agentpmt": {
      "type": "streamable-http",
      "url": "https://api.agentpmt.com/mcp",
      "headers": {
        "Authorization": "Bearer <base64-encoded-credentials>"
      }
    }
  }
}
```

After installing, replace `YOUR_API_KEY` with your base64-encoded credentials (see [Encoding Credentials](#encoding-credentials) below).

#### Cline

Add to your Cline MCP settings with the same configuration format as above.

### <a id="encoding-credentials"></a>Encoding Credentials

Encode your API key and budget key as a base64 bearer token:

```bash
# Format: api_key:budget_key
echo -n "your-api-key:your-budget-key" | base64
```

Or use JSON format:

```bash
echo -n '{"api_key":"your-api-key","budget_key":"your-budget-key"}' | base64
```

Use the resulting base64 string as the Bearer token in the Authorization header.

### OAuth Authentication

AgentPMT also supports full OAuth 2.0 authentication. The OAuth metadata endpoint is available at:

```
https://api.agentpmt.com/.well-known/oauth-protected-resource
```

MCP clients that support OAuth will automatically discover the authorization server and initiate the flow.

## Available Tools

Once connected, your AI agent can access:

### Built-in Tools

| Tool | Description |
|------|-------------|
| `AgentPMT-Refresh-Tools` | Refresh the available tool list from the marketplace |
| `AgentPMT-Report-Tool-Issue` | Report issues with any tool to the AgentPMT team |

### Marketplace Tools

The full tool list is dynamically loaded based on your budget configuration. Tools span categories including:

- **Communication** - Email, messaging, notifications
- **Data & Analytics** - Data processing, visualization, reporting
- **Development** - Code generation, testing, deployment
- **File Management** - Storage, conversion, processing
- **Search & Research** - Web search, knowledge retrieval
- **Workflow Automation** - Task scheduling, orchestration
- And many more

Use `AgentPMT-Refresh-Tools` to see the latest available tools.

## API Reference

### MCP Protocol

AgentPMT implements the Model Context Protocol (MCP) specification version 2025-03-26.

**Supported Methods:**

| Method | Description |
|--------|-------------|
| `initialize` | Initialize connection and exchange capabilities |
| `tools/list` | List all available tools for your budget |
| `tools/call` | Execute a tool (may trigger a purchase) |
| `ping` | Health check |

### Session Management

- Sessions are automatically created on first authenticated request
- Sessions expire after 2 hours of inactivity
- Session IDs are returned in the `Mcp-Session-Id` response header

## Pricing

Tools on the AgentPMT marketplace have individual pricing set by vendors. Your budget controls how much your agents can spend. Visit [agentpmt.com](https://agentpmt.com) to:

- Browse available tools and pricing
- Set up budgets with spending limits
- Monitor agent spending in real-time
- Review purchase history and usage

## Support

- **Website:** [agentpmt.com](https://agentpmt.com)
- **Issues:** [GitHub Issues](https://github.com/Apoth3osis-ai/agentpmt-mcp-public/issues)

## Registry Listings

AgentPMT is registered on the [Official MCP Registry](https://registry.modelcontextprotocol.io) as `com.agentpmt/agentpmt`.

## License

Proprietary - All rights reserved.
