<p align="center">
  <a href="https://sline.dev" target="_blank" rel="noopener noreferrer">
    <img width="180" src="https://sline.dev/sline-logo.png" alt="Sline logo">
  </a>
</p>
<br/>
<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="npm package"></a>
  <a href="https://nodejs.org/"><img src="https://img.shields.io/badge/node-%3E%3D18-brightgreen"></a>
  <a href="https://sline.dev/mcp"><img src="https://img.shields.io/badge/Status-Third%20Party-orange"/></a>
</p>

# SHOPLINE Dev MCP (Third-Party Development)

> **⚠️ Important Notice**: Currently, SHOPLINE has not officially released any MCP services. This MCP is a third-party developer initiative. This project aims to provide AI development assistant solutions for the SHOPLINE ecosystem and hopes for official support in developing related features.

**Third-party MCP server providing community-driven SHOPLINE development resources.** The SHOPLINE Dev Model Context Protocol (MCP) server enables your AI assistant to access community documentation, template conversion tools, and development guidance for the SHOPLINE ecosystem.

## 🤖 How it works

Your AI assistant uses the MCP server to access community-compiled SHOPLINE development resources:

1. **Ask your AI assistant** to help with SHOPLINE development tasks or Sline template work
2. **The assistant searches** community documentation and resources based on your prompt
3. **The MCP server provides** access to third-party documentation, template tools, and community knowledge to help with SHOPLINE development

## 📋 Requirements

Before you set up the Dev MCP server, make sure you have:

- **Node.js 18 or higher** installed on your system
- **An AI development tool** that supports MCP, such as Cursor or Claude Desktop

## 💬 What you can ask your AI assistant

After you set up the MCP server, you can ask your AI assistant questions like:

- "How do I create a product using the Admin API?"
- "What fields are available on the Order object?"
- "Show me an example of a webhook subscription"
- "How do I authenticate my SHOPLINE app?"
- "What's the difference between Admin API and Storefront API?"
- "How do Sline templates differ from Liquid?"
- "Validate this Sline template syntax for me"
- "What are the available Sline filters and tags?"
- "How to create a custom theme section?"

Your AI assistant will use the MCP server to search SHOPLINE's documentation when providing responses.

## 🛠️ Supported APIs (Third-Party Implementation)

The MCP server provides tools to interact with the following SHOPLINE APIs (Hoping for official support):

- **[Admin GraphQL API](https://sline.dev/mcp/docs/api/admin-graphql)** - Complete store management and data access (Third-party documentation)
- **[Storefront API](https://sline.dev/mcp/docs/api/storefront)** - Customer-facing commerce operations (Third-party documentation) 
- **[Webhook API](https://sline.dev/mcp/docs/api/webhooks)** - Real-time event notifications (Third-party documentation)
- **[Sline Template Engine](https://sline.dev/sline-template.html)** - SHOPLINE's template language for themes
- **[Theme Development Tools](https://sline.dev/mcp/docs/themes)** - Theme validation and optimization (Third-party documentation)
- **[Basic App Development Guidance](https://sline.dev/mcp/docs/app-basics)** - Fundamental app development concepts (Third-party documentation, Hoping for official support)

## ⚙️ Set up the server

The server runs locally in your development environment and doesn't require authentication.

### Step 1: Run the server

Open a new terminal window and run the following command. Keep this terminal window open while using the server:

```bash
npx -y @slinedev/dev-mcp@latest
```

### Step 2: Configure your AI development tool

Add configuration code that tells your AI tool how to connect to and use the Dev MCP server. This configuration enables your AI assistant to automatically access SHOPLINE documentation, API schemas, and development guidance when you ask questions.

#### Cursor

1. Open Cursor and go to `Cursor > Settings > Cursor Settings > Tools and integrations > New MCP server`
2. Add this configuration to your MCP servers:

```json
{
  "mcpServers": {
    "shopline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@slinedev/dev-mcp@latest"]
    }
  }
}
```

> **Note**: For more information, see the [Cursor MCP documentation](https://docs.cursor.com/context/model-context-protocol).

3. If you see connection errors on Windows, try this alternative configuration:

```json
{
  "mcpServers": {
    "shopline-dev-mcp": {
      "command": "cmd",
      "args": ["/k", "npx", "-y", "@slinedev/dev-mcp@latest"]
    }
  }
}
```

#### Claude Desktop

1. Open Claude Desktop and access your configuration file through settings
2. Add this configuration to your MCP servers section:

```json
{
  "mcpServers": {
    "shopline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@slinedev/dev-mcp@latest"]
    }
  }
}
```

> **Note**: For more information, read the [Claude Desktop MCP guide](https://modelcontextprotocol.io/quickstart/user).

3. Save your configuration and restart your AI development tool

### Step 3: (Optional) Configure advanced options

The Dev MCP server supports several advanced configuration options:

#### Disable instrumentation

This package makes instrumentation calls to better understand how to improve the MCP server. To disable them, set the `OPT_OUT_INSTRUMENTATION` environment variable:

```json
{
  "mcpServers": {
    "shopline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@slinedev/dev-mcp@latest"],
      "env": {
        "OPT_OUT_INSTRUMENTATION": "true"
      }
    }
  }
}
```

#### Enable Sline support

To access Sline template engine documentation and validation tools, add an `env` block with the `SLINE` flag to your MCP server configuration:

```json
{
  "mcpServers": {
    "shopline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@slinedev/dev-mcp@latest"],
      "env": {
        "SLINE": "true"
      }
    }
  }
}
```

You can also control the validation mode by setting `SLINE_VALIDATION_MODE`:

- `"full"` (default): Enables the `validate_theme` tool for validating entire theme directories
- `"partial"`: Enables the `validate_theme_codeblocks` tool for validating individual codeblocks

```json
{
  "mcpServers": {
    "shopline-dev-mcp": {
      "command": "npx",
      "args": ["-y", "@slinedev/dev-mcp@latest"],
      "env": {
        "SLINE": "true",
        "SLINE_VALIDATION_MODE": "partial"
      }
    }
  }
}
```

> **Beta**: This is a developer preview of Sline support. This documentation will be updated as we release new features.

## 🛠️ Available tools

The Dev MCP server provides the following tools:

### 📚 `learn_shopline_api` (Third-Party Implementation, Hoping for official support)

Provides guidance about SHOPLINE APIs based on available third-party documentation and community knowledge. This tool accesses [sline.dev/mcp](https://sline.dev/mcp/) to provide development guidance for working with SHOPLINE APIs.

> **Note**: This tool provides third-party documentation and guidance. For official API documentation, please refer to SHOPLINE's official developer resources.

### 🔍 `search_docs_chunks` (Third-Party Implementation, Hoping for official support)

Search across community-compiled [sline.dev/mcp](https://sline.dev/mcp/) documentation to find relevant information matching your query. Results are based on third-party documentation and may have incomplete context.

**Best for**: General research across multiple development topics, though individual results may lack full context.

### 📄 `fetch_full_docs` (Third-Party Implementation, Hoping for official support)

Retrieve complete documentation for specific paths from [sline.dev/mcp](https://sline.dev/mcp/). Provides community-compiled documentation without chunking, based on available public information.

**Choose this when**: You need comprehensive details from third-party documentation sources.

### 🔬 `introspect_admin_schema` (Community Implementation, Hoping for official support)

Explore available SHOPLINE API information based on community documentation and public resources. Helps developers understand API structure based on third-party analysis.

**Note**: This is based on community research and may not reflect complete or current API schemas.

### ✅ `validate_graphql_codeblocks` (Basic Validation, Hoping for official support)

Provides basic validation of GraphQL code blocks against common patterns and syntax rules. This is not connected to official SHOPLINE schemas.

**Use when**: You need basic syntax checking for GraphQL code.

### 🎨 `validate_theme_codeblocks`

Validates individual Sline codeblocks and supporting theme files (JSON, CSS, JS, SVG) to ensure correct syntax and references.

**Ideal for**: Incremental theme development - validates individual templates and catches syntax errors, undefined objects, and broken file references.

> **Note**: Requires `SLINE=true` and `SLINE_VALIDATION_MODE=partial` in your MCP server configuration. See Enable Sline support for setup instructions.

### 🏗️ `validate_theme`

Validates entire theme directories using SHOPLINE's Theme Check to detect errors in Sline syntax, missing references, and other theme issues.

**Run this on**: Complete themes to catch cross-file issues and ensure consistency. Applies all Theme Check rules for comprehensive validation.

> **Note**: Requires `SLINE=true` and `SLINE_VALIDATION_MODE=full` in your MCP server configuration. See Enable Sline support for setup instructions.

## 🔖 Available prompts

This MCP server provides the following prompts:

| Prompt | Description |
|--------|-------------|
| `shopline_admin_graphql` | Create Admin API GraphQL operations |
| `sline_template_development` | Build and validate Sline templates |
| `shopline_theme_structure` | Generate proper theme folder structure |

## 💬 Development Examples

After setting up the MCP server, you can ask your AI assistant questions like:

### 🚀 API Development Examples
```
"How do I create a product using the Admin API?"
"What fields are available on the Order object?"
"Show me an example of a webhook subscription"
"How do I authenticate my SHOPLINE app?"
"What's the difference between Admin API and Storefront API?"
"How do I handle pagination in GraphQL queries?"
"Show me bulk operation examples"
"What are common API usage patterns?"
```

### 🎨 Sline Template Development Examples
```
"How do Sline templates differ from Liquid?"
"Validate this Sline template syntax for me"
"How to create loops in Sline templates?"
"What are the available Sline filters?"
"Show me Sline tag examples"
"How to create a custom theme section?"
"What's the proper theme folder structure?"
"How to add theme settings and configurations?"
"Best practices for responsive theme design"
"How to include theme assets properly?"
```

### 🔧 App Development Examples
```
"How to create a SHOPLINE app from scratch?"
"What are the required app configurations?"
"Basic app development concepts and patterns"
"App development best practices from community"
"How to structure a SHOPLINE app project?"
"What are the fundamental app requirements?"
```

### 🔄 Migration & Integration Examples
```
"How to migrate from Shopify to SHOPLINE?"
"What are the main differences in API structure?"
"How to convert Liquid templates to Sline?"
"Basic integration patterns for third-party services"
"Template migration considerations"
"Platform differences and migration planning"
```

## 💡 Tips for Better AI Assistance

### 🎯 Be Specific
- Include your programming language and framework
- Mention your specific use case or goal
- Specify the SHOPLINE API you're working with
- Include your current tech stack and constraints

### 📝 Request Examples
- Ask for complete, working code snippets
- Request step-by-step implementation guides
- Ask for best practices and security considerations
- Request testing and debugging strategies

### 🐛 Troubleshooting
- Include full error messages and stack traces
- Share relevant code snippets causing issues
- Describe your expected vs actual behavior
- Mention what you've already tried

### 🔄 Migration Help
- Specify your current platform (e.g., Shopify)
- Describe your existing architecture
- Ask about equivalent SHOPLINE features
- Request migration timeline and strategies

## 🏗️ Technical Specifications

### Protocol Support
- **Model Context Protocol (MCP) 1.0**
- **JSON-RPC 2.0** interface
- **Local server** deployment
- **Cross-platform** compatibility (Windows, macOS, Linux)
- **Community-maintained** documentation access

### Documentation Coverage (Third-Party Implementation)
- Admin GraphQL API (Hoping for official support)
- Storefront API (Hoping for official support)
- Webhook API (Hoping for official support)
- Sline Template Engine (Official)
- Theme Development (Third-party guidance)

### Development Features (Third-Party Implementation)
- Community-compiled API documentation (Hoping for official support)
- Basic code validation and syntax checking (Hoping for official support)
- Development best practices guidance (Community-driven)
- Template conversion tools (Sline ↔ Liquid)
- Community support and discussions

### Supported AI Tools
- Cursor IDE with MCP support
- Claude Desktop application
- Any MCP-compatible AI client
- Custom development environments
- VS Code extensions (planned)

### Language Support
- **English (en)** - Primary documentation language
- **Simplified Chinese (zh-CN)** - Chinese documentation
- **Other languages** - Community contributions welcome

## 🔄 How It Works Workflow

Your AI assistant uses the SHOPLINE Dev MCP server through this workflow:

1. **Ask Questions** - Ask your AI assistant about SHOPLINE development tasks or Sline template creation
2. **Search Community Documentation** - The assistant searches community-compiled documentation and resources
3. **Get Guidance** - Receive development guidance based on available third-party documentation and community knowledge

> **Note**: This MCP provides community-driven documentation and guidance. For official support and latest API information, please refer to SHOPLINE's official developer resources.

## 📞 Related resources

### Updates (Third-Party Resources)
- [Developer Changelog](https://sline.dev/mcp/changelog) - Latest features and improvements (Third-party)
- [SHOPLINE Partners Community](https://partners.shoplineapp.com) - Connect with other developers (Official)
- [SHOPLINE Developer Blog](https://developers.shoplineapp.com/blog) - Technical insights and tutorials (Official)

### Business growth
- [SHOPLINE Partners Program](https://www.shoplineapp.com/partners) - Monetize your development skills (Official)
- [SHOPLINE App Store](https://apps.shoplineapp.com) - Publish and distribute your apps (Official)
- [SHOPLINE Academy](https://academy.shoplineapp.com/developers) - Learn platform development (Official)

### Development Tools (Third-Party)
- [Sline Template Converter](https://sline.dev/mcp/docs/converter) - Convert between template formats (Third-party)
- [Storefront MCP](https://sline.dev/storefront-mcp.html) - MCP server for storefront operations (Third-party)
- [Sline Template Engine](https://sline.dev/sline-template.html) - SHOPLINE's template language documentation (Official)
- [Community Tools](https://sline.dev/mcp/docs/tools) - Developer tools and utilities (Community-driven)

## 🤝 Contributing

We welcome contributions to improve SHOPLINE Dev MCP! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Setup

1. Clone the repository from [GitHub](https://github.com/slinedev/shopline-dev-mcp)
2. Install dependencies: `npm install`
3. Run in development mode: `npm run dev`
4. Run tests: `npm test`

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

##  Support

- 📖 [Documentation](https://sline.dev/mcp/)
- 🐛 [Issue Tracker](https://github.com/slinedev/sline-dev-mcp/issues)
- 💬 [Discussions](https://github.com/slinedev/sline-dev-mcp/discussions)
- 🌐 [SHOPLINE Platform](https://shoplineapp.com) (Official)

## 🙏 Acknowledgments

- [Model Context Protocol](https://modelcontextprotocol.io) - The protocol that makes this possible
- [SHOPLINE Platform](https://shoplineapp.com) - The e-commerce platform we're building for

---

**Connect your AI assistant to SHOPLINE's development resources and accelerate your development workflow!**

*Built with ❤️ by the Third-Party SHOPLINE Developer Community at sline.dev*
