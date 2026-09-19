<p align="center">
  <img src="assets/logo.png" alt="BalkanID" width="64">
</p>

# BalkanID MCP Server

Connect Claude, Cursor, VS Code, ChatGPT, and other [MCP](https://modelcontextprotocol.io)-compatible
clients to your BalkanID tenant — query identity access, entitlements, non-human identities (NHI),
and run access reviews directly from your AI assistant.

This repository is a **distribution and reference repo**, not the server implementation. The
BalkanID MCP Server is a hosted, remote service at `https://mcp.balkanid.app`; there is nothing to
build or run from this repo. It holds the client manifests, the MCP registry entry
([`server.json`](./server.json)), and setup documentation.

> **Early Access.** BalkanID MCP is currently an Early Access capability and must be enabled for
> your tenant. Contact [support@balkan.id](mailto:support@balkan.id) to request enablement.

## What you can do with it

- Look up who has access to what, across integrated applications and systems
- Search and inspect identities, including non-human identities (service accounts, AI agents)
- Run and review User Access Review (UAR) campaigns
- Create, approve, reject, or delegate access requests
- Manage JIT/PBAC access constraints
- Query BalkanID product documentation directly from your assistant

See [Tools](#tools) below for how to get the current tool list.

## Quick setup

**Server URL:** `https://mcp.balkanid.app/server/mcp` (streamable HTTP)

The fastest path for any supported client is the one-click flow: open
[mcp.balkanid.app](https://mcp.balkanid.app), sign in, confirm the correct **tenant**, then under
**OAuth Connectors** choose your client. Manual configuration for each client is below.

Full setup guides, including screenshots, live at
[docs.balkan.id/balkanid-mcp](https://docs.balkan.id/balkanid-mcp).

### Claude

Claude Desktop, Claude Code, and claude.ai all connect to the same remote endpoint.

1. In Claude, go to **Settings → Connectors → Add custom connector**.
2. Enter the server URL: `https://mcp.balkanid.app/server/mcp`
3. Complete the BalkanID sign-in and grant consent.

See [Claude Desktop](https://docs.balkan.id/balkanid-mcp/installation-and-setup/claude-desktop) and
[Claude Code](https://docs.balkan.id/balkanid-mcp/installation-and-setup/claude-code) guides.

### Cursor

Add to your Cursor MCP configuration:

```json
{
  "BalkanID MCP Server": {
    "url": "https://mcp.balkanid.app/server/mcp",
    "type": "http"
  }
}
```

Cursor prompts for OAuth sign-in on first use.
[Full guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/cursor).

### VS Code

```json
{
  "servers": {
    "balkanid": {
      "url": "https://mcp.balkanid.app/server/mcp",
      "type": "http"
    }
  }
}
```

[Full guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/vs-code).

### ChatGPT

Requires **Developer Mode** (or equivalent connector access on your plan). Confirm this is allowed
under your organization's AI policy before connecting to a production BalkanID tenant.

1. In ChatGPT, go to **Settings → Connectors** and add a custom connector.
2. Enter the server URL: `https://mcp.balkanid.app/server/mcp`
3. Complete the BalkanID OAuth sign-in.

[Full guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/chatgpt).

### Microsoft Copilot and Perplexity

See the
[Microsoft Copilot](https://docs.balkan.id/balkanid-mcp/installation-and-setup/microsoft-copilot)
and [Perplexity](https://docs.balkan.id/balkanid-mcp/installation-and-setup/perplexity) guides.

### Verifying a connection

Ask your assistant: *"Call whoami on BalkanID MCP."* You should see your email and tenant ID.

### API key (Bearer token) auth

For clients that need a static Bearer token instead of OAuth, generate one in the MCP UI at
[mcp.balkanid.app](https://mcp.balkanid.app) under **Bearer Auth Keys**, then send it as:

```
Authorization: Bearer YOUR_TOKEN_HERE
```

For example, in Cursor:

```json
{
  "BalkanID MCP Server": {
    "url": "https://mcp.balkanid.app/server/mcp",
    "type": "http",
    "headers": {
      "Authorization": "Bearer YOUR_TOKEN_HERE"
    }
  }
}
```

## Authentication

The BalkanID MCP Server supports two authentication modes:

- **OAuth 2.1** (preferred) — the server acts as an OAuth resource server. Dynamic Client
  Registration (DCR) is supported, so Claude, ChatGPT, Cursor, and VS Code can complete sign-in
  without manual client registration. Scopes: `read`, `write`, `offline_access`.

  > OAuth currently requests both Read and Write scopes together; a read-only OAuth connection is
  > not yet available. Use a read-scoped Bearer key if you need read-only access today.

- **API keys** — static Bearer tokens generated in the MCP UI under **Bearer Auth Keys**, for
  clients that don't support the OAuth flow.

Discovery endpoints:
- [`/.well-known/oauth-protected-resource/server/mcp`](https://mcp.balkanid.app/.well-known/oauth-protected-resource/server/mcp)
- [`/.well-known/oauth-authorization-server`](https://mcp.balkanid.app/.well-known/oauth-authorization-server)

## Tools

The tool set changes as the server evolves, so it isn't listed here to avoid drifting out of date.
Once connected, ask your assistant to run the server's `help` tool for the current list, or see the
[tool reference](https://docs.balkan.id/balkanid-mcp) in the docs. Every tool is annotated read-only
or write, so clients that support it will prompt for confirmation before a write action.

## Prerequisites

- An active BalkanID tenant **with MCP enabled** (Early Access — contact
  [support@balkan.id](mailto:support@balkan.id) to request enablement).
- A BalkanID user account with a role appropriate to the tools you intend to use — Reviewer, Risk
  Manager, or Administrator, depending on the operation. The MCP server does not grant any access
  beyond what your BalkanID role already allows.
- An MCP-compatible AI client.

## Documentation, privacy, and support

- Full setup guides: [docs.balkan.id/balkanid-mcp](https://docs.balkan.id/balkanid-mcp)
- Privacy policy: [docs.balkan.id/terms-and-conditions/privacy-policy](https://docs.balkan.id/terms-and-conditions/privacy-policy)
- Terms of service: [docs.balkan.id/terms-and-conditions/terms-of-service](https://docs.balkan.id/terms-and-conditions/terms-of-service)
- Support: [support@balkan.id](mailto:support@balkan.id)

## Security

This server enforces your existing BalkanID role-based permissions — an assistant connected via MCP
can only see and do what the authenticated user is already authorized for.

To report a vulnerability, see [SECURITY.md](./SECURITY.md). Please don't open a public issue for
security problems — email [security@balkan.id](mailto:security@balkan.id) instead.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) and our [Code of Conduct](./CODE_OF_CONDUCT.md). This repo
is maintained by the owners listed in [CODEOWNERS](./CODEOWNERS).

## License

[Apache License 2.0](./LICENSE)
