---
name: "agentpmt"
displayName: "AgentPMT"
description: "Universal MCP marketplace that gives AI agents instant access to a growing library of tools, workflows, and automations through a single connection."
keywords: ["marketplace", "automation", "workflows", "tool-orchestration", "ai-agents", "mcp"]
author: "Apoth3osis AI"
---

# AgentPMT

AgentPMT is the universal MCP marketplace that gives AI agents instant access to a growing library of tools, workflows, and automations. Rather than coding individual integrations, your agents discover and execute capabilities on demand through a single MCP connection -- from SaaS platform access and API orchestration to complete business process automation.

## Core Concepts

AgentPMT acts as a single MCP endpoint that dynamically provides tools from its marketplace. When connected, agents can browse, purchase, and execute tools without any additional setup. Tools are loaded based on your budget configuration and can span any category -- communication, data processing, file management, development, and more.

### Credit-Based Purchasing

Agents use credit allocations to purchase and execute tools and workflows on demand. Purchases can also be made via x402 stablecoin if authorized. All spending is controlled through configurable budgets.

### Encrypted Credential Management

Agents can use encrypted credentials to access software platforms and make credit card purchases without ever having access to the actual credentials. All credit card flows have a human in the loop via the mobile app approval process.

### Central Dashboard

All agent interactions are tracked in the central dashboard for easy troubleshooting and prompt engineering flows, providing end-to-end visibility into agent activity.

## Common Workflows

### Discovering Available Tools

Once connected, use the `AgentPMT-Refresh-Tools` tool to load the latest marketplace tools into your session. Tools are dynamically loaded based on your budget configuration.

### Executing a Tool

Call any marketplace tool by name. If the tool requires a purchase, it will be charged to your budget automatically (within your configured spending limits).

### Reporting Issues

Use `AgentPMT-Report-Tool-Issue` to report any problems with marketplace tools directly to the AgentPMT team.

## MCP Config Placeholders

The `mcp.json` file uses the following placeholder:

- `{{AGENTPMT_BEARER_TOKEN}}` - Your encoded API credentials. To obtain this value:
  1. Create an account at [agentpmt.com](https://agentpmt.com)
  2. Set up a budget with spending limits
  3. Generate an API key and budget key
  4. Encode them: `echo -n "your-api-key:your-budget-key" | base64`
  5. Use the resulting base64 string as your bearer token

## Troubleshooting

### Connection Issues

- Verify your bearer token is correctly base64-encoded
- Ensure your API key and budget key are both valid
- Check that your budget has available credits

### Tools Not Loading

- Call `AgentPMT-Refresh-Tools` to reload the tool list
- Verify your budget has tools enabled
- Check your budget spending limits have not been exceeded

### Session Expiry

Sessions expire after 2 hours of inactivity. Reconnect and re-authenticate to start a new session.

## License and Support

This power integrates with [AgentPMT](https://agentpmt.com).

- [Support](https://agentpmt.com)
- [GitHub Issues](https://github.com/Apoth3osis-ai/agentpmt-mcp-public/issues)
