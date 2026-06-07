# Variant MCP

Variant MCP is the official Model Context Protocol integration for Variant, an AI-native presentation editor for HTML/CSS slide decks.

Use the hosted Variant MCP server to let MCP-compatible clients create decks, inspect slides, make targeted edits, render previews, manage brand context, and export presentations.

> The production MCP server is hosted by Variant. This public repository is a surface-level integration guide for setup, examples, and discoverability. It does not contain the private Variant backend implementation.

## Quick Start

Connect your MCP client to:

```txt
https://mcp.variant.art/mcp
```

For clients that support remote HTTP MCP servers and OAuth, use:

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

Restart your MCP client, then ask it to list your Variant decks. The client should launch the Variant OAuth flow when it needs authorization.

For headless setups, generate a scoped token in Variant and add it as a bearer token:

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

## What Is The Variant MCP Server?

The Variant MCP server exposes presentation-aware tools over the Model Context Protocol. Instead of asking an AI assistant to guess how to edit a slide file, the assistant can call structured tools such as `deck.create`, `slide.get`, `slide.edit`, `slide.preview`, and `deck.export`.

Variant decks are HTML/CSS-native, so agents can work with real slide source while humans keep a visual editor for layout cleanup and review.

## What Can Agents Do?

With the right scopes, an MCP client can:

- List and read decks.
- Create new decks or duplicate an existing deck.
- Read slide content, metadata, selected elements, and revisions.
- Apply targeted slide edits without regenerating the whole deck.
- Batch-create, replace, update, or delete slides.
- Render slide previews as PNG or JPEG.
- Upload deck or brand assets.
- Read and update brand context.
- List and update comments.
- Export decks to supported output formats.

## Tools

The hosted server currently exposes these MCP tools:

| Tool | Purpose |
| --- | --- |
| `decks.list` | List accessible decks with slide counts and open URLs. |
| `deck.get` | Get deck metadata, theme, revision, URLs, and optional asset aliases. |
| `deck.create` | Create or duplicate a deck. |
| `deck.update` | Update deck title or theme. |
| `deck.replaceAllSlides` | Replace the full slide list. |
| `deck.versions.list` | List recent saved deck versions. |
| `deck.version.restore` | Restore a saved deck version. |
| `deck.listSlides` | List slide numbers, titles, sizes, formats, revisions, and URLs. |
| `slides.batchUpdate` | Create, replace, update, or delete multiple slides in order. |
| `slide.get` | Get slide metadata, optional content, selected elements, and URLs. |
| `slide.edit` | Apply revision-guarded edits to a slide or slide elements. |
| `slide.duplicate` | Duplicate a slide. |
| `slide.move` | Move a slide. |
| `slide.replace` | Replace one slide wholesale. |
| `slide.preview` | Render a slide preview as PNG or JPEG. |
| `selection.get` | Return the editor's latest selected slide and element IDs. |
| `asset.upload` | Upload deck or brand assets. |
| `deck.export` | Start a deck export and return status or a download URL. |
| `comments.list` | List deck comments. |
| `comments.update` | Create, update, resolve, or delete comments. |
| `brand.context` | Read workspace brand guidelines and brand assets. |
| `brand.update` | Update brand guidelines or brand asset metadata. |

See [docs/tools.md](docs/tools.md) for workflow guidance.

## Scopes

Variant MCP credentials can be scoped:

- `deck:read`
- `deck:write`
- `slide:replace`
- `slide:preview`
- `export:run`

Use the smallest scope set that fits the client. Read-only review, slide editing, and export automation should not share the same credential by default.

## Client Examples

- [Claude Code](examples/claude-code.json)
- [Claude Desktop](examples/claude-desktop.json)
- [Cursor](examples/cursor.json)
- [Codex](examples/codex.md)

## Documentation

- [Quickstart](docs/quickstart.md)
- [Authentication](docs/authentication.md)
- [Tools](docs/tools.md)
- [Prompt examples](docs/prompts.md)
- [Schema summary](docs/schema-summary.md)
- [Use cases](docs/use-cases.md)
- [Troubleshooting](docs/troubleshooting.md)
- [FAQ](docs/faq.md)
- [Claude Code](docs/clients/claude-code.md)
- [Cursor](docs/clients/cursor.md)
- [Codex](docs/clients/codex.md)

## Links

- Variant: https://variant.art
- Canonical Variant MCP page: https://variant.art/mcp
- Setup guide: https://variant.art/docs/mcp
- Tools reference: https://variant.art/docs/mcp-tools
- App: https://app.variant.art
- Hosted MCP endpoint: https://mcp.variant.art/mcp
- Model Context Protocol: https://modelcontextprotocol.io

## Support

Open an issue in this repository for documentation gaps, setup problems, and client-specific examples. Do not post tokens, deck contents, private prompts, or account secrets.

For account-specific access problems, use Variant support from the app.
