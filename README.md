# Sline Dev MCP Server

This project implements a Model Context Protocol (MCP) server that interacts with Sline Dev. This protocol supports various tools to interact with different SHOPLINE APIs. At the moment the following APIs are supported:

- Admin GraphQL API
- Functions
- (Optional) Polaris Web Components

## Setup

To run the Sline MCP server using npx, use the following command:

```bash
npx -y @sline/dev-mcp@latest
```

## Usage with Cursor or Claude Desktop

Add the following configuration. For more information, read the [Cursor MCP documentation](https://docs.cursor.com/context/model-context-protocol) or the [Claude Desktop MCP guide](https://modelcontextprotocol.io/quickstart/user).

```json
{
  "mcpServers": {
    "sline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@sline/dev-mcp@latest"]
    }
  }
}
```

On Windows, you might need to use this alternative configuration:

```json
{
  "mcpServers": {
    "sline-dev-mcp": {
      "command": "cmd",
      "args": ["/k", "npx", "-y", "@sline/dev-mcp@latest"]
    }
  }
}
```

### Disable instrumentation

In order to better understand how to improve the MCP server, this package makes instrumentation calls. In order to disable them you can set the `OPT_OUT_INSTRUMENTATION` environment variable. In Cursor or Claude Desktop the configuration would look like this:

```json
{
  "mcpServers": {
    "sline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@sline/dev-mcp@latest"],
      "env": {
        "OPT_OUT_INSTRUMENTATION": "true"
      }
    }
  }
}
```

### Opt-in Polaris support (experimental)

If you want Cursor or Claude Desktop to surface Polaris Web Components documentation, include an `env` block with the `POLARIS_UNIFIED` flag in your MCP server configuration:

```json
{
  "mcpServers": {
    "sline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@sline/dev-mcp@latest"],
      "env": {
        "POLARIS_UNIFIED": "true"
      }
    }
  }
}
```
