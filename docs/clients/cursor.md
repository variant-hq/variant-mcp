# Cursor And Variant MCP

Use Variant MCP with Cursor when you want an AI coding agent to work directly with Variant decks from your editor.

Canonical setup guide: https://variant.art/docs/cursor-mcp

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

Restart Cursor after changing MCP config.

## First Prompt

```txt
Connect to Variant, list my decks, list the slides in the most recently updated deck, and preview slide 1. Do not edit anything.
```

## Editing Prompt

```txt
Read slide 3, identify the headline element, make the headline shorter with slide.edit, and preview the result.
```

