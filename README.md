# Coconut Claude Code plugins

Public marketplace for Coconut's Claude Code plugins.

| Plugin | What it does |
|---|---|
| [`coco-context`](https://github.com/lovelybunch/coco-context) | Connects Claude Code to Coconut Context — search, read, and write pages and spaces, and manage scheduled agent tasks. |

## Install

```bash
/plugin marketplace add lovelybunch/coco-plugins
```

```bash
/plugin install coco-context@coco
```

`coco-context` prompts for **Coco MCP endpoint** at enable time, defaulting to
`https://api.coconut.md/mcp`. See the
[plugin README](https://github.com/lovelybunch/coco-context) for authentication
and troubleshooting.

## Layout

This repository holds only the catalog. Each plugin lives in its own repository
and is referenced here by a `github` source, so plugin releases are independent
of marketplace changes.

```
.claude-plugin/marketplace.json   ← the catalog
```

## Adding a plugin

1. Create the plugin in its own public repository, with
   `.claude-plugin/plugin.json` at the repository root.
2. Add an entry to `.claude-plugin/marketplace.json` with a `url` source
   giving that repository's full `https://` clone URL. Do **not** use a
   `github` source: Claude Code expands those to `git@github.com:owner/repo.git`
   and the install fails for anyone without a GitHub SSH key.
3. Validate both, then push:

```bash
claude plugin validate . --strict
```

Pin a release by adding `ref` or `sha` to the source. Without a pin, installs
track the plugin repository's default branch.
