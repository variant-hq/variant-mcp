# AGENTS.md

## Scope

This repo is the public documentation and example surface for Variant MCP.

The production MCP server implementation is not in this repository. It remains in Variant's internal monorepo under `apps/mcp-server` and `packages/mcp-contract`.

## Rules

- Keep this repository surface-level: setup docs, client examples, tool summaries, troubleshooting, and AEO/SEO-friendly explanations.
- Do not add private backend code, deployment config, database/storage details, internal environment variables, secrets, tokens, or dashboard exports.
- Treat `https://mcp.variant.art/mcp` as the public hosted endpoint.
- Use HTTP transport examples. Do not describe Variant MCP as a local `stdio` server.
- When updating tool names, scopes, or auth behavior, verify against the internal Variant MCP contract before changing public docs.
- Do not publish private deck content, private prompts, customer names, bearer tokens, or OAuth tokens in examples.

## Public Positioning

Describe Variant MCP as the official hosted MCP integration for Variant, an AI-native presentation editor for HTML/CSS slide decks.

Do not imply that this repo contains the full open-source server implementation.

