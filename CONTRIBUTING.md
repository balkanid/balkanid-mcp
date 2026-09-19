# Contributing

This repository is a **distribution and reference repo** for the BalkanID MCP Server — it contains
the server manifest (`server.json`), setup documentation, and tool reference. It does not contain
the server's source code, so there is nothing to build, run, or test here.

## What contributions are welcome

- Fixes to setup instructions (broken config snippets, outdated client steps)
- Corrections to the tool reference table
- Improvements to clarity, links, or formatting in `README.md`
- Reports of stale or incorrect information

## What doesn't belong here

- Feature requests for the MCP server itself (new tools, behavior changes) — these should go to your
  BalkanID account team or [support@balkan.id](mailto:support@balkan.id), since this repo doesn't
  contain the server implementation.
- Security vulnerabilities — do not open a public issue. Email
  [security@balkan.id](mailto:security@balkan.id) instead.

## Making a change

1. Open an issue describing the problem before submitting a pull request, unless the fix is trivial
   (typo, dead link).
2. Keep pull requests scoped to a single change.
3. For changes to `server.json`, validate against the
   [MCP server schema](https://static.modelcontextprotocol.io/schemas/2025-12-11/server.schema.json)
   before submitting.

All changes are reviewed by the maintainers listed in [`CODEOWNERS`](./CODEOWNERS).
