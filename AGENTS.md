# Research notes — Zephex CLI only

## Identity

- Surface: **local terminal Mode 2**
- Binary / package: `zephex` (npm), install via `https://zephex.dev/cli/install.sh`
- Project model: **cwd** (or `--cwd` / `--path github:…`)
- Agent orientation: `zephex deep --json` → `schema_version: 1`
- Same credits as MCP `https://zephex.dev/mcp`

## Agent install recipe

1. `curl -fsSL https://zephex.dev/cli/install.sh | bash`  
2. `cd <project>`  
3. `zephex login`  
4. `zephex deep --json`  
5. After edits: `zephex test` → `check test failures` / `fix-prompt`

## Differentiator

| Repo | Question it answers |
|------|---------------------|
| **This** | How do I run Zephex in a shell? |
| zephex-MCPs | How do I attach tools inside an editor? |
| zephex-web-terminal | How do I try Mode 2 without installing? |

Do not invent flags — use `zephex <cmd> --help` or https://zephex.dev/docs/cli-commands.
