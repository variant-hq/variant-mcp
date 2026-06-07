# Troubleshooting

## The Client Cannot Connect

Check that the config uses HTTP transport:

```json
{
  "transport": "http",
  "url": "https://mcp.variant.art/mcp"
}
```

Variant's hosted MCP endpoint is not a local command and does not use `stdio`.

## OAuth Does Not Start

Restart the client after changing config. Many MCP clients only load server entries at startup.

If the browser flow is blocked by a VPN, proxy, or remote container, use a bearer token instead.

## `decks.list` Returns Nothing

Common causes:

- The token is scoped to the wrong workspace.
- The account has no decks in Variant.
- The credential has insufficient read access.

## The Agent Rewrites Too Much

Ask for a targeted edit:

```txt
Use slide.edit. Change only the selected title element. Do not replace the whole slide.
```

Whole-slide replacement is useful for drafts, but targeted edits are better for preserving layout.

## Preview Is Blank Or Slow

Preview rendering depends on slide assets, fonts, and runtime behavior. Try:

- Previewing a simpler slide.
- Checking whether an image or font upload is still pending.
- Reducing preview width or scale.
- Retrying after a rate-limit window.

## Export Fails

Check that the credential includes export access and that required assets are available. If the deck was edited moments ago, preview one slide first to confirm rendering is healthy.

## Do Not Share Secrets

When opening an issue, remove:

- Bearer tokens.
- OAuth tokens.
- Deck IDs for private decks.
- Private deck content.
- Customer names or confidential prompts.

