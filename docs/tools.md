# Variant MCP Tools

Variant exposes presentation-aware MCP tools so agents can work with decks directly.

## Deck Tools

| Tool | Use |
| --- | --- |
| `decks.list` | Find accessible decks. |
| `deck.get` | Read deck metadata, theme, revision, URLs, and assets. |
| `deck.create` | Create a blank or demo deck, or duplicate an existing deck. |
| `deck.update` | Update the title or theme. |
| `deck.replaceAllSlides` | Replace every slide in a deck. |
| `deck.versions.list` | List recent deck versions. |
| `deck.version.restore` | Restore a saved version. |
| `deck.trash` | Move a deck to the trash. |
| `deck.recover` | Recover a deck from the trash. |
| `deck.shareLinks.list` | List a deck's active share links. |
| `deck.shareLinks.create` | Create a share link and return its viewer URL. |
| `deck.shareLinks.revoke` | Revoke a share link. |
| `deck.activity.list` | Read recent deck activity. |
| `deck.listSlides` | Get slide summaries for a deck. |
| `deck.export` | Export a deck. Pass `async: true` to run the export as a background job. |
| `deck.export.status` | Check the status of an export job. |

## Slide Tools

| Tool | Use |
| --- | --- |
| `slide.get` | Read slide content, metadata, selected elements, and revision information. |
| `slide.edit` | Apply targeted edits to a slide or element. |
| `slide.duplicate` | Duplicate a slide. |
| `slide.move` | Move a slide to a new position. |
| `slide.replace` | Replace one slide wholesale. |
| `slide.versions.list` | List saved versions of one slide. |
| `slide.version.restore` | Restore a saved slide version. |
| `slide.preview` | Render a slide preview image. |
| `slides.batchUpdate` | Create, replace, update, or delete multiple slides in one ordered call. |
| `selection.get` | Read the currently selected slide and elements from the editor. |

## Asset, Brand, And Comment Tools

| Tool | Use |
| --- | --- |
| `asset.upload` | Upload images, fonts, PDFs, or other supported assets. |
| `brand.context` | Read workspace brand guidelines and brand assets. |
| `brand.update` | Update guidelines or brand asset metadata. |
| `comments.list` | List deck comments. |
| `comments.update` | Create, update, resolve, or delete comments. |

## Recommended Agent Pattern

For edits, ask the agent to:

1. Call `deck.get` or `deck.listSlides`.
2. Call `slide.get` with the relevant slide number.
3. Identify the target element.
4. Call `slide.edit` with a small patch.
5. Call `slide.preview` to visually verify the change.

This is usually better than replacing a whole slide. Reserve `slide.replace`, `deck.replaceAllSlides`, and broad `slides.batchUpdate` calls for new drafts, structural rewrites, or controlled regeneration.

## Sharing And Exporting

- `deck.shareLinks.create` returns a view-only URL anyone can open. Only the deck owner can create or revoke share links, and creating a new link replaces the previous one.
- `deck.export` renders PDF and PPTX exports synchronously by default, which can take a while for large decks. Pass `async: true` to get a job ID back immediately, then poll `deck.export.status` until the job completes.

## Errors And Revisions

Write tools are revision-guarded. If a slide or deck changed since you read it, the tool call fails with a `STALE_REVISION` error that includes the current deck and slide revisions, so you can re-read and retry without extra round trips.

