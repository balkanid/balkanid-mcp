<p align="center">
  <img src="assets/logo.png" alt="BalkanID" width="96">
</p>

<h1 align="center">BalkanID MCP Server</h1>

<p align="center">
  <b>The official Model Context Protocol (MCP) server for BalkanID: a cloud-hosted bridge that gives your AI tools secure, real-time access to your identity and access graph — entitlements, non-human identities, access reviews, and requests.</b>
</p>

<!-- Line 1 · Project -->
<p align="center">
  <a href="https://github.com/balkanid/balkanid-mcp"><img src="https://img.shields.io/badge/Official-BalkanID-6C4FE0?logoColor=white" alt="Official BalkanID Server"></a>
  <a href="https://github.com/balkanid/balkanid-mcp/stargazers"><img src="https://img.shields.io/github/stars/balkanid/balkanid-mcp?style=flat&logo=github&label=Stars&color=6C4FE0" alt="GitHub stars"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/balkanid/balkanid-mcp?label=License&color=6C4FE0" alt="License: Apache 2.0"></a>
  <a href="https://docs.balkan.id/balkanid-mcp"><img src="https://img.shields.io/badge/Status-Early_Access-F5A623" alt="Status: Early Access"></a>
</p>

<!-- Line 2 · Protocol & access -->
<p align="center">
  <a href="https://modelcontextprotocol.io"><img src="https://img.shields.io/badge/Model_Context_Protocol-compatible-000000?logo=modelcontextprotocol&logoColor=white" alt="Model Context Protocol compatible"></a>
  <a href="server.json"><img src="https://img.shields.io/badge/MCP_Registry-app.balkanid-000000?logo=modelcontextprotocol&logoColor=white" alt="MCP Registry: app.balkanid"></a>
  <a href="#authentication"><img src="https://img.shields.io/badge/Auth-OAuth_2.1%20%7C%20Bearer_token-2EBC4F" alt="Auth: OAuth 2.1 or Bearer token"></a>
  <a href="https://mcp.balkanid.app"><img src="https://img.shields.io/badge/Hosting-BalkanID_Cloud-6C4FE0?logoColor=white" alt="Hosting: BalkanID Cloud"></a>
</p>

<p align="center">
  <a href="https://docs.balkan.id/balkanid-mcp/getting-started-with-mcp"><b>Getting started</b></a> ·
  <a href="#tools">Tools</a> ·
  <a href="#security">Security &amp; admin</a> ·
  <a href="mailto:support@balkan.id">Support</a>
</p>

---

The **official BalkanID MCP Server** is a cloud-hosted bridge between your BalkanID tenant and compatible AI tools. Once connected, it lets those tools see and act on **identities, entitlements, non-human identities, access reviews, requests, and employee records** in real time. Authentication uses **OAuth 2.1** or a **Bearer token**, so every action respects the connected user's existing BalkanID role and permissions.

With the BalkanID MCP Server, you can:

* **Look up** who has access to what, across every connected application and system.
* **Inspect** identities, including non-human identities like service accounts and AI agents.
* **Run and act on** User Access Review (UAR) campaigns — approve, deny, or delegate reviews.
* **Create and manage** permanent or temporary (JITPBAC) access requests and their approvals.
* **Look up, create, and update** employee records.
* **Ask** BalkanID's own documentation questions and get sourced answers.

Connect once, then describe what you want — no tab switching between your assistant and the BalkanID app.

It's built for security, IT, and compliance teams running access certifications, investigating over-provisioned access, or managing identity lifecycle from an AI assistant or IDE.

> [!IMPORTANT]
> BalkanID MCP is currently an **Early Access** capability and must be enabled for your tenant. Contact [support@balkan.id](mailto:support@balkan.id) to request enablement before following the setup steps below.

## One-click setup

Pick your AI client below to connect the BalkanID MCP Server. Each button uses your client's native install link, so you don't need to edit any JSON config by hand.

<table align="center">
  <tr>
    <td align="center" width="180">
      <a href="https://cursor.com/en/install-mcp?name=BalkanID&config=eyJ1cmwiOiJodHRwczovL21jcC5iYWxrYW5pZC5hcHAvc2VydmVyL21jcCJ9">
        <img src="https://img.shields.io/badge/Cursor-000000?style=for-the-badge&logo=cursor&logoColor=white" alt="Add to Cursor"><br>
        <b>Add to Cursor</b>
      </a>
      <br><sub>Query access and entitlements from your editor.</sub>
    </td>
    <td align="center" width="180">
      <a href="https://vscode.dev/redirect/mcp/install?name=BalkanID&config=%7B%22url%22%3A%22https%3A%2F%2Fmcp.balkanid.app%2Fserver%2Fmcp%22%2C%22type%22%3A%22http%22%7D">
        <img src="https://img.shields.io/badge/VS_Code-0098FF?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0iI2ZmZmZmZiI+PHBhdGggZD0iTTE3LjUgMiA5LjIgOS42IDQuNiA2LjEgMyA2Ljl2MTAuMmwxLjYuOCA0LjYtMy41IDguMyA3LjZMMjEgMjFWM3pNNi40IDEybDIuOS0yLjJ2NC40em0xMS4xIDQuOS01LjQtNC45IDUuNC00Ljl6Ii8+PC9zdmc+&logoColor=white" alt="Add to VS Code"><br>
        <b>Add to VS Code</b>
      </a>
      <br><sub>Query access and entitlements via GitHub Copilot.</sub>
    </td>
    <td align="center" width="180">
      <a href="https://docs.balkan.id/balkanid-mcp/installation-and-setup/chatgpt">
        <img src="https://img.shields.io/badge/ChatGPT-10A37F?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0iI2ZmZmZmZiI+PHBhdGggZD0iTTEyIDIgMyA3djEwbDkgNSA5LTVWN3ptMCAyLjMgNi41IDMuNkwxMiAxMS41IDUuNSA3Ljl6TTUgOS42bDYgMy4zdjYuOGwtNi0zLjN6bTE0IDB2Ni44bC02IDMuM3YtNi44eiIvPjwvc3ZnPg==&logoColor=white" alt="Add to ChatGPT"><br>
        <b>Add to ChatGPT</b>
      </a>
      <br><sub>Official listing pending &mdash; see setup guide.</sub>
    </td>
    <td align="center" width="180">
      <a href="https://docs.balkan.id/balkanid-mcp/installation-and-setup/claude-desktop">
        <img src="https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=claude&logoColor=white" alt="Add to Claude"><br>
        <b>Add to Claude</b>
      </a>
      <br><sub>Official listing pending &mdash; see setup guide.</sub>
    </td>
  </tr>
</table>

> The ChatGPT and Claude buttons above link to manual setup guides until the official directory
> submissions for both are approved. Cursor and VS Code install directly today.

### Let your agent do the setup

Most AI coding agents can configure the server themselves. Copy and paste this prompt into your agent:

```
Set up BalkanID MCP for this agent using the official setup guide at
https://docs.balkan.id/balkanid-mcp/getting-started-with-mcp
and the MCP server URL https://mcp.balkanid.app/server/mcp. Then start the BalkanID
authentication flow so I can sign in.
```

Or add the server manually with your client's own command:

| Client | Command or configuration |
| --- | --- |
| Claude Code | `claude mcp add --transport http balkanid https://mcp.balkanid.app/server/mcp`, then run `/mcp` in a session to authenticate |
| Claude Desktop | **Settings → Connectors → Add custom connector**, then enter the server URL |
| VS Code / GitHub Copilot | Command Palette → **MCP: Add Server**, or add to `.vscode/mcp.json` |
| Cursor | Add to `.cursor/mcp.json`, or install via the [Cursor Marketplace](#one-click-setup) button above |
| ChatGPT | **Settings → Connectors → Add custom connector** (requires Developer Mode) |
| Any other MCP client | Use the server URL `https://mcp.balkanid.app/server/mcp` (streamable HTTP) |

> [!TIP]
> For the current, canonical setup steps per client, see
> [Getting started with the BalkanID MCP Server](https://docs.balkan.id/balkanid-mcp/getting-started-with-mcp).

## Contents

* [One-click setup](#one-click-setup)
* [Supported clients](#supported-clients)
* [Plugin packaging and compatibility](#plugin-packaging-and-compatibility)
* [What you can do with it today](#what-you-can-do-with-it-today)
* [Authentication](#authentication)
* [Tools](#tools)
* [Prerequisites](#prerequisites)
* [Documentation, privacy, and support](#documentation-privacy-and-support)
* [Security](#security)
* [Contributing](#contributing)
* [License](#license)

---

## Supported clients

The BalkanID MCP Server works with a growing list of MCP-compatible clients:

| Client | Setup reference |
| --- | --- |
| Claude (Claude.ai, Desktop, and Code) | [Claude setup guides](https://docs.balkan.id/balkanid-mcp/installation-and-setup/claude-desktop) |
| Cursor | [Cursor setup guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/cursor) |
| Visual Studio Code (GitHub Copilot) | [VS Code setup guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/vs-code) |
| OpenAI ChatGPT | [ChatGPT setup guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/chatgpt) |
| Microsoft 365 Copilot / Teams | [Microsoft Copilot setup guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/microsoft-copilot) |
| Perplexity | [Perplexity setup guide](https://docs.balkan.id/balkanid-mcp/installation-and-setup/perplexity) |
| Any other MCP client | Use the server URL `https://mcp.balkanid.app/server/mcp` (streamable HTTP) |

> [!TIP]
> For the current, canonical list of supported clients and step-by-step setup, see
> [Getting started with the BalkanID MCP Server](https://docs.balkan.id/balkanid-mcp/getting-started-with-mcp).
> You can also refer to your client's own MCP documentation.

---

## Plugin packaging and compatibility

This repository publishes the same MCP server in several package formats so clients can use their native discovery and installation flows:

| Format | Manifest and configuration |
| --- | --- |
| [Agent Plugins](https://agent-plugins.org/) | [`plugin.json`](plugin.json) and [`mcp.json`](mcp.json) |
| Claude Code plugin | [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json) and [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) |
| Cursor plugin | [`.cursor-plugin/plugin.json`](.cursor-plugin/plugin.json) |
| Gemini extension | [`gemini-extension.json`](gemini-extension.json) |
| MCP Registry | [`server.json`](server.json) |

Both `mcp.json` and `.mcp.json` are intentional. Agent Plugins requires the root `mcp.json` filename
and its portable transport vocabulary; existing clients continue to use `.mcp.json` and their native
configuration vocabulary. Keep their endpoint settings aligned when changing either file.

---

## What you can do with it today

- **Discovery** — look up identities, connections, resources, credentials, and integrations across
  every connected system, and trace how they relate to one another
- **Access reviews** — list and act on User Access Review (UAR) campaign items: approve, deny, or
  delegate
- **Requests** — create permanent or temporary (JITPBAC) access requests, and manage their
  approval workflow
- **HRIS** — look up, create, and update employee records
- **Docs** — ask BalkanID's documentation questions and get sourced answers

All actions are scoped to your existing BalkanID role permissions — a connected assistant can only
see or do what the authenticated user is already authorized for.

## Authentication

The BalkanID MCP Server supports two authentication modes:

- **OAuth 2.1** (preferred) — the server acts as an OAuth resource server. Dynamic Client
  Registration (DCR) and Client ID Metadata Documents (CIMD) are both supported, so Claude, ChatGPT,
  Cursor, and VS Code can complete sign-in without manual client registration. Scopes: `read`,
  `write`, `offline_access`.

  > OAuth currently requests both Read and Write scopes together; a read-only OAuth connection is
  > not yet available. Use a read-scoped Bearer key if you need read-only access today.

- **Bearer token** — a static token generated in the MCP UI under **Bearer Auth Keys**, for clients
  that don't support the OAuth flow.

Discovery endpoints:
- [`/.well-known/oauth-protected-resource/server/mcp`](https://mcp.balkanid.app/.well-known/oauth-protected-resource/server/mcp)
- [`/.well-known/oauth-authorization-server`](https://mcp.balkanid.app/.well-known/oauth-authorization-server)

### Bearer token setup

For clients that need a static token instead of OAuth, generate one in the MCP UI at
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

### Verifying a connection

Ask your assistant: *"Call whoami on BalkanID MCP."* You should see your email and tenant ID.

## Tools

The tool set changes as the server evolves, so it isn't listed exhaustively here to avoid drifting
out of date. Once connected, ask your assistant to run the server's `help` tool for the current list
scoped to your role, or see the
[getting started guide](https://docs.balkan.id/balkanid-mcp/getting-started-with-mcp). Every tool is
annotated read-only or write, so clients that support it will prompt for confirmation before a write
action.

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

Model Context Protocol (MCP) lets AI agents connect to tools and BalkanID data using your account's
permissions, which creates powerful workflows but also structural risks. Any MCP client or server
you enable (IDE plugins, desktop apps, hosted MCP servers, or "one-click" integrations) can cause an
AI agent to perform actions on your behalf.

Large language models are vulnerable to
[prompt injection](https://owasp.org/www-community/attacks/PromptInjection) and related attacks
(indirect prompt injection, tool poisoning). These attacks can instruct an agent to exfiltrate data
or make unintended changes without an explicit request.

To reduce risk: only use trusted MCP clients and servers, review which tools and data each agent can
access, and apply least privilege (a read-scoped Bearer key where you don't need write access). For
any high-impact or destructive action, require human confirmation and monitor your BalkanID audit
logs for unusual activity.

This server enforces your existing BalkanID role-based permissions — an assistant connected via MCP
can only see and do what the authenticated user is already authorized for.

To report a vulnerability, see [SECURITY.md](./SECURITY.md). Please don't open a public issue for
security problems — email [security@balkan.id](mailto:security@balkan.id) instead.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) and our [Code of Conduct](./CODE_OF_CONDUCT.md). This repo
is maintained by the owners listed in [CODEOWNERS](./CODEOWNERS).

## License

[Apache License 2.0](./LICENSE)
