# Codex And Variant MCP

Use Variant MCP with Codex when you want Codex to create, inspect, edit, and export HTML/CSS slide decks.

Canonical setup guide: https://variant.art/docs/codex-mcp

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
Create a three-slide product update deck in Variant. Preview slide 2 after creating it and tighten the headline if it looks too long.
```

## Export Prompt

```txt
Export this Variant deck as HTML for browser review and PPTX for client handoff.
```

