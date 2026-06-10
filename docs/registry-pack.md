# Variant MCP — Registry Metadata Pack

The single source of truth for submitting Variant MCP to directories and
registries. Copy from here so every listing stays consistent. Update this file
on every release that changes tools, auth, or links — stale listings hurt
trust more than missing ones.

## Identity

| Field | Value |
| --- | --- |
| Server name | Variant MCP |
| Registry name | `art.variant/variant` |
| Endpoint | `https://mcp.variant.art/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.0 (PKCE) for interactive clients; scoped bearer tokens for headless |
| OAuth discovery | `https://mcp.variant.art/.well-known/oauth-authorization-server` |
| Scopes | `deck:read`, `deck:write`, `slide:replace`, `slide:preview`, `export:run` |
| Vendor | Variant — https://variant.art |
| Homepage | https://variant.art/mcp |
| Docs | https://variant.art/docs/mcp |
| Repository | https://github.com/variant-hq/variant-mcp |
| License (this repo) | MIT |
| Pricing | Free tier; paid Team and Studio plans |
| Categories | Presentations, Productivity, Design, Developer Tools |
| Keywords | presentations, slides, decks, html, claude-code, codex, cursor, export, pptx |

## One-line description (under 80 chars)

> Create, edit, preview, and export presentation decks with AI agents.

## Short description (~160 chars, for meta/directory cards)

> Hosted MCP server for Variant, the AI-native presentation editor. Agents
> create HTML slide decks, edit single elements, render previews, and export
> to PDF or PPTX.

## 100-word description

> Variant is an AI-native presentation editor where every slide is real HTML
> and CSS. The Variant MCP server gives agents like Claude Code, Cursor, and
> Codex 22 structured tools to create decks, edit individual slides and
> elements, render PNG previews for visual QA, upload assets, read brand
> guidelines, manage comments, and export to HTML, PDF, or PPTX. Agents work
> in a loop — read state, make a targeted edit, preview the result — instead
> of regenerating whole decks. Humans refine the same decks on a visual
> canvas. Hosted endpoint with OAuth or scoped bearer tokens; free tier
> available.

## Install commands per client

Claude Code:

```sh
claude mcp add --transport http variant https://mcp.variant.art/mcp
```

Claude Desktop / generic JSON config ([examples/claude-desktop.json](../examples/claude-desktop.json)):

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

Cursor ([examples/cursor.json](../examples/cursor.json)) and Codex
([examples/codex.md](../examples/codex.md)) use the same JSON block. For
headless setups, add `"headers": {"Authorization": "Bearer <token>"}` with a
scoped token generated in Variant ([examples/bearer-token.json](../examples/bearer-token.json)).

First prompt to verify a connection:

```txt
List my Variant decks, choose the most recently updated deck, list its slides,
and preview slide 1. Do not edit anything.
```

## Tool list (22 tools)

| Tool | One-liner |
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

## Assets

- Logo (SVG): [assets/logo.svg](../assets/logo.svg)
- Logo (PNG): [assets/logo.png](../assets/logo.png)
- Social/OG card: [assets/og.png](../assets/og.png)
- Screenshots: [assets/screenshots/](../assets/screenshots/)
- Demo GIF: not yet recorded. Suggested script: terminal running
  `claude mcp add --transport http variant https://mcp.variant.art/mcp`, then a
  prompt building a 5-slide deck from a README, ending on the deck open in the
  Variant canvas. Keep it under 60 seconds, landscape.

## Submission checklist

| Registry | How to submit | Status |
| --- | --- | --- |
| Official MCP registry | `mcp-publisher` CLI with [server.json](../server.json); requires DNS or HTTP domain verification for the `art.variant` namespace | Ready — server.json committed |
| Smithery | smithery.ai — add as external/remote server pointing at the hosted endpoint | Not submitted |
| Glama | glama.ai/mcp/servers — claim via GitHub repo | Not submitted |
| PulseMCP | pulsemcp.com — submission form | Not submitted |
| mcp.so | Submission form / GitHub issue | Not submitted |
| mcpservers.org | PR against their repo | Not submitted |
| SkillsLLM | skillsllm.ai submission (security-scans within ~24h) | Not submitted |
| Cursor Directory | Uses [.plugin/plugin.json](../.plugin/plugin.json) and [.mcp.json](../.mcp.json) | Metadata committed |
| awesome-mcp-servers | PR adding Variant under a Presentations/Productivity category; one line: name, link, one-line description | Not submitted |

When a listing goes live, record the URL here so release updates can touch
every listing.

## Boilerplate

> Variant is an AI-native presentation editor. Slides are real HTML and CSS:
> agents generate and edit them over MCP, humans refine them on a visual
> canvas, and decks export as HTML, PDF, or PPTX. Built for workflows where
> Claude Code, Cursor, or Codex own the deck.
