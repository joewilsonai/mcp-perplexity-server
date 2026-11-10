# Perplexity MCP Server

**Perplexity-backed code analysis and debugging, straight from your Claude conversation.**

A small [Model Context Protocol](https://modelcontextprotocol.io) server that gives Claude Desktop (or any MCP client) one tool: send an error or coding question, plus optional code, to the Perplexity API and get back a structured answer.

<a href="https://glama.ai/mcp/servers/oxchzx8c75"><img width="380" height="200" src="https://glama.ai/mcp/servers/oxchzx8c75/badge" alt="Perplexity Server MCP server" /></a>

## Status

Last updated May 2026. Checked in November 2026: `npm ci` and `npm run build` succeed and the server starts and lists its tool. **Live answers from Perplexity will not work as shipped.** The code asks for the model `llama-3.1-sonar-huge-128k-online`, which [Perplexity's changelog](https://docs.perplexity.ai/changelog/changelog) says stopped being available on February 22, 2025. Perplexity now offers the Sonar models instead.

## Tool

### `search`

| Argument | Required | Description |
|---|---|---|
| `query` | yes | The error message or coding question |
| `code` | no | A code snippet to analyze |
| `language` | no | Language of the snippet, default `auto` |

The answer comes back in four sections: root cause analysis, step-by-step solution, best practices for prevention, and code examples (before, after, alternatives).

One built-in shortcut: if the code contains `item['price']`, or adds a quoted value to a number, the server returns a prewritten answer about a Python string-plus-integer `TypeError` without calling Perplexity, whatever the question was.

## Install

There is no npm package. Build from source with Node 18 or newer:

```bash
git clone https://github.com/joewilsonai/mcp-perplexity-server
cd mcp-perplexity-server
npm ci
npm run build
```

## Configure Claude Desktop

Add this to `claude_desktop_config.json`, with the absolute path to your clone and your own key:

```json
{
  "mcpServers": {
    "perplexity": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-perplexity-server/build/index.js"],
      "env": {
        "PERPLEXITY_API_KEY": "<your-perplexity-api-key>"
      }
    }
  }
}
```

The key is read from the `PERPLEXITY_API_KEY` environment variable only; the server will not start without it. Get a key from your [Perplexity API settings](https://www.perplexity.ai/settings/api).

## Built with

TypeScript, `@modelcontextprotocol/sdk` 0.6.0 and axios.

## License

MIT. See [LICENSE](LICENSE).
