<div align="center">

# 🔍 Perplexity MCP Server

**Perplexity-backed code analysis and debugging — straight from your Claude conversation.**

A Model Context Protocol (MCP) server that lets Claude (or any MCP client) ask Perplexity AI for code analysis, error explanations, and debugging help.

[![MCP](https://img.shields.io/badge/MCP-Server-d97757)](https://modelcontextprotocol.io)
[![Stars](https://img.shields.io/github/stars/joewilsonai/mcp-perplexity-server?style=social)](https://github.com/joewilsonai/mcp-perplexity-server/stargazers)
[![Node](https://img.shields.io/badge/Node-18+-339933?logo=node.js)](https://nodejs.org)
[![License](https://img.shields.io/badge/License-MIT-blue)](#license)

<a href="https://glama.ai/mcp/servers/oxchzx8c75"><img width="380" height="200" src="https://glama.ai/mcp/servers/oxchzx8c75/badge" alt="Perplexity Server MCP server" /></a>

</div>

---

## Features

- 🐛 **Intelligent Error Analysis** — Root-cause breakdown of coding errors
- 🔬 **Pattern Detection** — Recognizes common error patterns and provides targeted solutions
- ✅ **Comprehensive Solutions** — Step-by-step fixes with multiple implementation alternatives
- 📚 **Best Practices** — Coding standards and error-prevention tips
- 🐍 **Python Support** — Specialized handling of Python type errors and common issues

## Example usage

Ask Claude:

> *"Fix this TypeError in my Python code"*
> *"What's causing this error message?"*
> *"How do I fix this code?"*

Include your code snippet:

```python
def calculate_total(items):
    total = 0
    for item in items:
        total = total + item['price']  # TypeError: string + int

data = [
    {'name': 'Book', 'price': '10'},
    {'name': 'Pen', 'price': '2'}
]

result = calculate_total(data)
```

The server returns:

1. **Root-cause analysis** of the error
2. **Step-by-step solution** with code examples
3. **Best practices** to prevent the same issue
4. **Alternative implementations**

## Install

### From npm (recommended)

```bash
npm install -g mcp-perplexity-server
```

### From source

```bash
git clone https://github.com/joewilsonai/mcp-perplexity-server
cd mcp-perplexity-server
npm install
npm run build
```

## Configure in Claude Desktop

Edit `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "perplexity": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-perplexity-server/build/index.js"],
      "env": {
        "PERPLEXITY_API_KEY": "your-perplexity-api-key"
      }
    }
  }
}
```

Get a Perplexity API key at [perplexity.ai/settings/api](https://perplexity.ai/settings/api).

## Prerequisites

- **Node.js 18 or higher**
- **A Perplexity AI API key**

## Stack

- **TypeScript** + **Node.js 18+**
- **@modelcontextprotocol/sdk**
- **Perplexity API**

## Related MCP servers

- 🧠 **[second-opinion-mcp-server](https://github.com/joewilsonai/second-opinion-mcp-server)** (⭐ 16) — Multi-source: Gemini + Perplexity + Stack Overflow
- 🐙 **[github-meta-mcp-server](https://github.com/joewilsonai/github-meta-mcp-server)** — Natural-language GitHub repo management

## License

MIT
