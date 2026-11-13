<div align="center">
  <img src="assets/emblem-256.png" alt="ZoZoPeak emblem: a gold dolphin leaping over a gold coin inside a laurel wreath" width="120">
</div>

# ZoZoPeak Coupon MCP Server

Free remote MCP server that gives AI assistants verified coupon codes and current store deals. No API key, no sign-up, nothing to install.

[![Glama](https://glama.ai/mcp/connectors/com.zozopeak/coupons/badges/score.svg)](https://glama.ai/mcp/connectors/com.zozopeak/coupons)
![MCP Registry](https://img.shields.io/badge/MCP%20Registry-com.zozopeak%2Fcoupons-blue)

**Server URL:** `https://mcp.zozopeak.com/mcp` (Streamable HTTP, no auth)

**Website and full guide:** [https://zozopeak.com/mcp](https://zozopeak.com/mcp) · **Docs:** [https://zozopeak.github.io/coupon-mcp-server/](https://zozopeak.github.io/coupon-mcp-server/)

## Connect

The server is remote and speaks Streamable HTTP. There is nothing to install: point your client at the server URL above.

### Claude (web and desktop)

1. Open **Settings → Connectors**.
2. Choose **Add custom connector**.
3. Name it **ZoZoPeak** and paste the server URL.
4. Choose the option that needs no sign-in and save.
5. In a chat, open the tools or connectors picker and enable ZoZoPeak.

### Claude Code

```bash
claude mcp add --transport http zozopeak https://mcp.zozopeak.com/mcp
```

### ChatGPT

1. Open **Settings → Connectors** and create a custom connector.
2. Paste the server URL and pick the option with no authentication.
3. Enable the connector in a chat, then ask for coupons by store.

### Cursor

Add the server to `mcp.json` (the same shape as [examples/cursor-mcp.json](examples/cursor-mcp.json)):

```json
{
  "mcpServers": {
    "zozopeak": {
      "url": "https://mcp.zozopeak.com/mcp"
    }
  }
}
```

### VS Code

Save [examples/vscode-mcp.json](examples/vscode-mcp.json) as `.vscode/mcp.json` in your workspace:

```json
{
  "servers": {
    "zozopeak": {
      "type": "http",
      "url": "https://mcp.zozopeak.com/mcp"
    }
  }
}
```

### Other clients over stdio

Clients that only speak stdio can bridge to the server with `mcp-remote` (same shape as [examples/stdio-mcp-remote.json](examples/stdio-mcp-remote.json)):

```json
{
  "mcpServers": {
    "zozopeak": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.zozopeak.com/mcp"]
    }
  }
}
```

## Tools

Both tools are read-only: they look up offers and return them, and they never write or change anything anywhere.

| Tool | Parameters | What it returns |
|---|---|---|
| `find_coupons` | `store` (string, required) · `country` (string, optional) · `limit` (integer, optional) | Coupon codes for the named store, each with an offer title, a stated discount and a link |
| `find_store_deals` | `store` (string, required) · `country` (string, optional) · `limit` (integer, optional) | Deal links for the named store, each with an offer title and a stated discount |

## Example prompts

- "Find coupon codes for AliExpress."
- "Find coupon codes for Noon in the UAE."
- "Find deal links for Amazon in the US."
- "Show me current deals for SHEIN."
- "Find coupons for Amazon and show the ones with the biggest stated saving."

## Links

- [ZoZoPeak coupon MCP server](https://zozopeak.com/mcp)
- [ZoZoPeak](https://zozopeak.com/)
- [Hot deals](https://zozopeak.com/hot-deals/)
- [Product comparisons](https://zozopeak.com/compare/)
- [Privacy](https://zozopeak.com/privacy#mcp)

## Support

Open an issue on [GitHub Issues](https://github.com/zozopeak/coupon-mcp-server/issues) or write to support@zozopeak.com.

## License

See [LICENSE.md](LICENSE.md).
