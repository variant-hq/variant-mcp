# Codex Example

Add Variant as a remote HTTP MCP server in the MCP configuration used by your Codex environment.

```json
{
  "mcpServers": {
    "variant": {
      "transport": "http",
      "url": "https://mcp.variant.art/mcp"
    }
  }
}
```

Then restart the client and test with:

```txt
List my Variant decks and preview the first slide of the most recently updated deck. Do not make edits.
```

For headless usage, use the bearer token example in [bearer-token.json](bearer-token.json).

