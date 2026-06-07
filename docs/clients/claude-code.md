# Claude Code And Variant MCP

Use Variant MCP with Claude Code when you want Claude to create, edit, preview, and export presentation decks from the terminal.

Canonical setup guide: https://variant.art/docs/claude-code-mcp

## OAuth Config

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

## First Prompt

```txt
List my Variant decks, choose the most recently updated deck, list its slides, and preview slide 1. Do not edit anything.
```

## Useful Follow-Up

```txt
On slide 1, change only the title text to "Q3 launch review". Use slide.edit, then preview the slide.
```

