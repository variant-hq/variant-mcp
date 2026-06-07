# Schema Summary

The hosted Variant MCP server returns full tool schemas from `tools/list`. This page is a human-readable summary, not a replacement for runtime schema introspection.

Canonical tools reference: https://variant.art/docs/mcp-tools

## Scopes

- `deck:read`
- `deck:write`
- `slide:replace`
- `slide:preview`
- `export:run`

## Deck Tools

- `decks.list`
- `deck.get`
- `deck.create`
- `deck.update`
- `deck.replaceAllSlides`
- `deck.versions.list`
- `deck.version.restore`
- `deck.listSlides`
- `deck.export`

## Slide Tools

- `slide.get`
- `slide.edit`
- `slide.duplicate`
- `slide.move`
- `slide.replace`
- `slide.preview`
- `slides.batchUpdate`
- `selection.get`

## Asset, Brand, And Comment Tools

- `asset.upload`
- `brand.context`
- `brand.update`
- `comments.list`
- `comments.update`

## Common Edit Pattern

1. Read the deck with `deck.get` or `deck.listSlides`.
2. Read the slide with `slide.get`.
3. Apply a targeted patch with `slide.edit`.
4. Render a visual check with `slide.preview`.
5. Export with `deck.export` when ready.

