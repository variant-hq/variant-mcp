# FAQ

## Is Variant MCP Open Source?

This public repository documents the hosted Variant MCP integration. The production server implementation is maintained in Variant's private/internal codebase.

## Is This A Local MCP Server?

No. Variant MCP is hosted at:

```txt
https://mcp.variant.art/mcp
```

Use HTTP transport.

## Which MCP Clients Work?

Any client that supports remote HTTP MCP servers should be able to connect. This repository includes examples for Claude Code, Claude Desktop, Cursor, and Codex-style workflows.

## Can Variant MCP Edit Existing Decks?

Yes, if the credential has write access. Agents can read slides, apply targeted edits, preview changes, and export the result.

## Can I Use Read-Only Access?

Yes. Use read-only scopes when you want an agent to summarize, review, or inspect decks without changing them.

## Does Variant MCP Export PPTX?

Variant supports presentation export workflows through `deck.export`. Available formats can depend on the current hosted service configuration.

## Is Variant A PowerPoint MCP Server?

No. Variant is an HTML/CSS-native presentation editor with MCP tools. It can support handoff formats, but the agent works against Variant decks rather than automating PowerPoint directly.

