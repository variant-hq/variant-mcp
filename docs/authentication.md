# Authentication

Variant MCP supports OAuth and scoped bearer tokens.

## OAuth

OAuth is the default for interactive clients. Add Variant's MCP endpoint to your client config and let the client discover the authorization metadata:

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

Use OAuth when:

- A person is using the client on their own machine.
- You want browser-based sign-in.
- You want session revocation tied to the account.

## Bearer Tokens

Bearer tokens are useful for headless and controlled environments:

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

Use bearer tokens when:

- The client cannot complete browser OAuth.
- The client runs in CI or a remote development environment.
- You want a credential with narrow scopes and easy revocation.

## Scopes

Variant credentials can include:

| Scope | Use |
| --- | --- |
| `deck:read` | Read deck metadata, slides, versions, comments, and brand context. |
| `deck:write` | Create or update decks, comments, selections, assets, and brand context. |
| `slide:replace` | Replace slides or full slide lists. |
| `slide:preview` | Render slide previews. |
| `export:run` | Export decks. |

Start with read-only access, then add write, preview, or export scopes as needed.

## Security Notes

- Do not commit bearer tokens.
- Do not share one token across a team.
- Revoke tokens when a machine, client, or workflow no longer needs access.
- Avoid pasting private deck content into public issues.

