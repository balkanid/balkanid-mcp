# Security policy

Thanks for helping keep the BalkanID MCP Server and the people who use it safe.

## Reporting a vulnerability

**Please don't open a public GitHub issue for a security problem.** Public issues are visible to
everyone and can put users at risk before a fix is ready.

Report it privately instead, to [security@balkan.id](mailto:security@balkan.id). A good report
usually includes:

- What you found, and why you think it's a security issue
- Steps to reproduce, or a proof of concept
- The affected component (a file in this repo, a client manifest, or the hosted endpoint)
- The impact you think it could have

## What this repository covers

This repo holds the public pieces of the BalkanID MCP Server: the documentation, the client
manifests (`.mcp.json`, `mcp.json`, `gemini-extension.json`, and the Claude and Cursor plugin
manifests), and the MCP registry entry (`server.json`).

The server itself is a hosted service at `mcp.balkanid.app`. Issues in the hosted service, in
authentication, or in the BalkanID platform go through the same
[security@balkan.id](mailto:security@balkan.id) process above. BalkanID maintains and updates the
hosted server, so there's nothing for you to patch on your end. Just connect to the current endpoint
documented in the [README](README.md).

## Using the MCP server safely

MCP lets an AI agent act in BalkanID with your permissions. That's useful, and it carries real risk.
Language models can be tricked by [prompt injection](https://owasp.org/www-community/attacks/PromptInjection)
and tool poisoning, where hidden instructions push an agent to leak data or make changes you never
asked for.

A few habits that lower the risk:

- Connect only to MCP clients and servers you trust.
- Use least privilege: scope Bearer keys to read-only unless write access is genuinely needed.
- Ask for human confirmation before any high-impact or destructive action.
- Watch your BalkanID audit logs for anything that looks off.

## Coordinated disclosure

Please give the security team a fair chance to investigate and ship a fix before you share details
publicly. We're grateful to researchers who report responsibly and work with us on timing.
