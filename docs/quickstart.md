# Variant MCP Quickstart

This guide connects an MCP-compatible client to the hosted Variant MCP server.

## Endpoint

```txt
https://mcp.variant.art/mcp
```

Use HTTP transport. Variant's hosted server is not a local `stdio` server.

## OAuth Setup

Use OAuth for interactive desktop clients:

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

Restart your client after changing its MCP config. Then ask:

```txt
List my Variant decks.
```

Your client should discover Variant's OAuth metadata and open a browser sign-in flow.

## Bearer Token Setup

Use bearer tokens for headless clients, CI, remote containers, or controlled access:

```json
{
  "mcpServers": {
    "variant": {
      "transport": "http",
      "url": "https://mcp.variant.art/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_VARIANT_MCP_TOKEN"
      }
    }
  }
}
```

Generate tokens in Variant with only the scopes the client needs.

## First Test

After connecting, run these checks in order:

1. Ask the client to list your Variant decks.
2. Ask it to open one deck and list its slides.
3. Ask it to read one slide with content included.
4. Ask it to preview that slide.
5. If the credential has write access, ask it to make one small targeted edit.
6. If the credential has export access, ask it to export the deck.

## A Good First Prompt

```txt
Connect to Variant, list my decks, choose the most recently updated deck, list its slides, and preview slide 1. Do not edit anything.
```

That exercises auth, deck reads, slide reads, and preview rendering without granting the agent permission to change your deck.

