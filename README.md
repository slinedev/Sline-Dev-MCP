# SHOPLINE Dev MCP (Third-Party Development)

<p align="center">
  <a href="https://sline.dev" target="_blank" rel="noopener noreferrer">
    <img width="120" src="https://sline.dev/sline-logo.png" alt="Sline logo">
  </a>
</p>

<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"></a>
  <a href="https://nodejs.org/"><img src="https://img.shields.io/badge/node-%3E%3D18-brightgreen" alt="Node.js"></a>
  <a href="https://sline.dev/mcp"><img src="https://img.shields.io/badge/Status-Third%20Party-orange" alt="Status"></a>
  <a href="https://modelcontextprotocol.io"><img src="https://img.shields.io/badge/MCP-1.0-blue" alt="MCP"></a>
</p>

> **⚠️ Important Notice**: This is a third-party developer initiative. SHOPLINE has not officially released any MCP services. This project hopes for official support in developing related features.

**Third-party MCP server providing community-driven SHOPLINE development resources.** The SHOPLINE Dev Model Context Protocol (MCP) server enables AI assistants to access community documentation, template conversion tools, and development guidance for the SHOPLINE ecosystem.

[View Demo](https://sline.dev/mcp) | [Third-Party Service](https://sline.dev/mcp)

## Features

### Core Capabilities
- **Sline Template Engine**: Official SHOPLINE template language documentation and tools
- **Community Documentation**: Third-party compiled API references and guides
- **Template Validation**: Syntax checking for Sline templates and theme files
- **Development Guidance**: Community-driven best practices and tutorials

### Third-Party Implementation Notes
- Built on publicly available SHOPLINE documentation
- Community-maintained with hopes for official support
- Limited by current public API access
- Template engine support is based on official Sline documentation

## Quick Start

### Prerequisites
- Node.js 18 or higher
- AI client that supports MCP (Claude Desktop, Cursor, etc.)

### Installation

Run the MCP server:
```bash
npx -y @slinedev/dev-mcp@latest
```

### Basic Configuration

#### Claude Desktop
Add to your MCP configuration:
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

#### Cursor
Add in Cursor settings:
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

### Advanced Configuration

#### Enable Sline Template Support
For Sline template validation and tools:
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

**Validation Modes:**
- `"full"`: Validate entire theme directories
- `"partial"`: Validate individual template files

#### Disable Telemetry
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

## API Reference

### Available MCP Tools

#### `learn_shopline_api` *(Third-Party Implementation)*
Provides guidance about SHOPLINE APIs based on community documentation.

**Note**: Results are based on third-party analysis and may not reflect current official APIs.

#### `search_docs_chunks` *(Third-Party Implementation)*
Search community-compiled documentation for relevant information.

**Best for**: General research across development topics with community insights.

#### `fetch_full_docs` *(Third-Party Implementation)*
Retrieve complete documentation pages from community sources.

**Use when**: You need comprehensive details from available third-party documentation.

#### `validate_theme_codeblocks`
Validates Sline template syntax and supporting files (CSS, JS, JSON).

**Requirements**: `SLINE=true` in configuration.

#### `validate_theme`
Validates entire theme directories using SHOPLINE's theme validation rules.

**Requirements**: `SLINE=true` and `SLINE_VALIDATION_MODE=full` in configuration.

## Usage Examples

### Sline Template Development
**Question:** "How do Sline templates differ from Liquid?"

The AI assistant will search community documentation to explain:
- Syntax differences between Sline and Liquid
- Available filters and tags
- Migration considerations
- Best practices for Sline development

### Template Validation
**Question:** "Validate this Sline template syntax"

```sline
{% for product in products %}
  <div class="product">
    <h3>{{ product.title }}</h3>
    <p>{{ product.price | money }}</p>
  </div>
{% endfor %}
```

The AI assistant will:
- Check Sline syntax validity
- Verify filter usage
- Identify potential issues
- Suggest improvements

### API Development Guidance
**Question:** "How do I create a product using the Admin API?"

The AI assistant will provide:
- Community-compiled API examples
- Basic GraphQL query structures
- Common patterns and best practices
- Third-party implementation notes

### Theme Development
**Question:** "What's the proper theme folder structure?"

The AI assistant will explain:
- SHOPLINE theme directory layout
- Required files and configurations
- Asset organization
- Development workflow

## Technical Specifications

- **Protocol:** Model Context Protocol (MCP)
- **Transport:** stdio
- **Source:** Community-maintained third-party project  
- **Documentation Format:** JSON-based resource management
- **Search Capabilities:** Semantic search across SHOPLINE docs
- **Coverage:** Sline template syntax, basic API patterns, theme structure

## Resources

**Development Resources:**
- [SHOPLINE Developer Platform](https://developers.shoplineapp.com) 
- [Sline Template Documentation](https://sline.dev)
- [SHOPLINE Admin API Reference](https://admin.api.shoplineapp.com) 
- [Theme Development Guide](https://developers.shoplineapp.com/themes)

**Community Resources:**
- [GitHub Repository](https://github.com/slinedev)
- [Issue Tracker](https://github.com//slinedev/)
- [Developer Community](https://developers.shoplineapp.com/community)

**Third-party Services:**
- [MCP Server Host](https://sline.dev/mcp) - Developer-maintained service
- [AI Development Assistant](https://sline.dev) - Community tools and resources

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

We welcome contributions from the SHOPLINE developer community:

1. Fork the repository
2. Create a feature branch
3. Add documentation or improvements  
4. Submit a pull request

## Support

For technical support:
- Create an issue on [GitHub](https://github.com/slinedev/)
- Visit the [SHOPLINE Developer Community](https://developers.shoplineapp.com/community)
- Check the [sline.dev documentation](https://sline.dev)

**Note:** This is a third-party community project. For official SHOPLINE API support, please contact SHOPLINE directly.
- [Sline Template Engine](https://sline.dev/sline-template.html) - SHOPLINE's template language documentation (Official)
- [Community Tools](https://sline.dev/mcp) - Developer tools and utilities (Community-driven)

## 🤝 Contributing

We welcome contributions to improve SHOPLINE Dev MCP! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Setup

1. Clone the repository from [GitHub](https://github.com/slinedev/sline-dev-mcp)
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
