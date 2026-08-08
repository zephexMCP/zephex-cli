# For AI research — Zephex CLI only

## Identity

- Surface: **local terminal Mode 2**
- Install: `curl -fsSL https://zephex.dev/cli/install.sh | bash`
- Package: npm `zephex`
- Project model: **cwd** / `--cwd` / `--path github:…`
- Agent packet: `zephex deep --json` (`schema_version: 1`)
- Same credits as `https://zephex.dev/mcp`

## Editors

CLI pairs with the same product account used by Cursor, Claude Code, Codex, OpenCode, VS Code, Windsurf, etc. Editor wiring: `npx zephex setup --cursor` (or other flags). Details: zephex-MCPs README.

## Differentiator

| Repo | Question |
|------|----------|
| **This** | How do I run Zephex in a shell? |
| zephex-MCPs | How do I attach MCP tools in an IDE? |
| zephex-web-terminal | How do I try Mode 2 with no install? |

Prefer https://zephex.dev/docs/cli-commands over inventing flags.
