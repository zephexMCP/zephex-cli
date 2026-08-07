# Zephex CLI

**Mode 2 for Zephex** — the same ten codebase tools as the hosted MCP, in your real terminal.

[![Website](https://img.shields.io/badge/website-zephex.dev-111?style=flat-square)](https://zephex.dev)
[![Install](https://img.shields.io/badge/install-one%20liner-0a0?style=flat-square)](https://zephex.dev/cli/install.sh)
[![Docs](https://img.shields.io/badge/docs-CLI-222?style=flat-square)](https://zephex.dev/docs/cli-commands)
[![MCP overview](https://img.shields.io/badge/MCP-zephex--MCPs-6e4?style=flat-square)](https://github.com/zephexMCP/zephex-MCPs)

```text
$ cd your-project
$ zephex login
$ zephex deep --json          # orientation packet for agents
$ zephex overview             # human briefing
$ zephex find "auth middleware"
$ zephex test && zephex check test failures
```

Same **API key** and **credits** as editor MCP (`https://zephex.dev/mcp`).  
Different **UX**: plain English (or `--json`), cwd-based project root, interactive `/` shell.

---

## Install (Mac / Linux)

```bash
curl -fsSL https://zephex.dev/cli/install.sh | bash
# same installer:
curl -fsSL https://zephex.dev/install.sh | bash
```

Bundles a runtime under `~/.zephex` when needed — no separate Node setup for most users.

### Windows (PowerShell)

```powershell
irm https://zephex.dev/install.ps1 | iex
```

### npm / npx

```bash
npx zephex setup
npx zephex --help
```

Package: [`zephex`](https://www.npmjs.com/package/zephex) · bins: `zephex`, `mcpcli`, …

---

## First 5 minutes

```bash
cd /path/to/your-app          # always — CLI uses cwd
zephex login                  # browser or paste key
zephex                        # interactive TUI — type /
# or one-shots:
zephex overview
zephex deep "add rate limiting"
zephex deep --json            # for AI agents
```

API keys: [zephex.dev/dashboard/api-keys](https://zephex.dev/dashboard/api-keys)

---

## Command map (what you’ll actually run)

### Orientation

| Command | Does | Notes |
|---------|------|--------|
| `zephex overview` | Plain-English project briefing | Lighter than deep |
| `zephex deep [task]` | Full dossier: stack + wiring + where to look | Optional task string |
| `zephex deep --json` | **Agent packet** `schema_version: 1` | `likely_touch`, plan, … |
| `zephex structure --agent` | Folder / language map | **0 credits** |
| `zephex architecture` | Module wiring | `--focus auth` |

### Search & read

| Command | Does |
|---------|------|
| `zephex find "…"` | Search (also `defs`, `rename`, `paste`) |
| `zephex read` / `summarize` / `outline` / `symbol` | Surgical file / symbol reads |

### Quality & packages

| Command | Does |
|---------|------|
| `zephex test` / `check test` | Run Test Pulse suite |
| `zephex check test failures` | Free session slice after a run |
| `zephex check test fix-prompt --copy` | Pasteable fix prompt for an agent |
| `zephex check test missing` | Sources without tests |
| `zephex safe <pkg>` | Package safety before install |
| `zephex check-package … --task upgrade` | Upgrade / migration intel |
| `zephex deps` | Scan direct dependencies |

### Other

| Command | Does |
|---------|------|
| `zephex check url https://…` | Live HTTPS audit (also `site`) |
| `zephex remember` / `recall` | Project memory |
| `zephex think "…"` | One-shot structured reasoning |
| `zephex docs "…"` | Expert playbooks (not private repo) |
| `zephex supply` | Supply Pulse (secrets / live bundles) |
| `zephex learn` | Free catalog of tools (no API call) |
| `zephex doctor` | Key, network, editor wiring |
| `zephex agent` | MCP vs CLI short guide |
| `zephex setup` / `connect` | Wire editors + CLI |

### Global flags (most hosted tools)

| Flag | Meaning |
|------|---------|
| `--json` | Agent / raw JSON |
| `--cwd <dir>` | Project root (monorepos) |
| `--path github:owner/repo` | Public remote repo |
| `--api-key` | Override key |
| `-q` / `--quiet` | Less noise |
| `--force` | Refresh caches |

Interactive slash: `/overview` · `/deep` · `/find` · `/structure` · `/test` · `/failures` · `/safe` · `/learn` · `/doctor` · `/quit`

Full reference: [zephex.dev/docs/cli-commands](https://zephex.dev/docs/cli-commands) · Deep guide: [zephex.dev/docs/deep](https://zephex.dev/docs/deep)

---

## CLI ↔ MCP tools

| CLI | MCP tool |
|-----|----------|
| overview / get-context / deep* | `get_project_context` (+ deep composites) |
| find / defs / rename | `find_code` |
| read / outline / symbol | `read_code` |
| architecture | `explain_architecture` |
| safe / check-package | `check_package` |
| test / check test * | `check_test` |
| check url / site | `audit_headers` |
| remember / recall | `project_memory` |
| think | `keep_thinking` |
| docs / ask | `Zephex_dev_info` |
| structure | free local layout |

\* `deep` chains several tools + local heuristics.

---

## For AI agents

When the user is in a **shell** or wants terminal Mode 2:

1. Ensure CLI is installed (`curl -fsSL https://zephex.dev/cli/install.sh | bash`).  
2. `cd` to their project (or pass `--cwd`).  
3. Prefer **`zephex deep --json`** for orientation (`schema_version: 1`).  
4. Prefer **MCP tool names** when Zephex is already connected in the editor.  
5. After edits: `zephex test` then free `check test failures` / `fix-prompt`.  
6. Do not invent CLI output if the binary is missing — ask them to install.  
7. Skill for editors: `npx skills add zephexMCP/agent-skills --skill zephex`

**Monorepo:** `zephex overview --cwd apps/web` or `cd apps/web` first.

---

## Related

| Repo | Role |
|------|------|
| [zephex-MCPs](https://github.com/zephexMCP/zephex-MCPs) | Hosted MCP overview (editors) |
| [zephex-web-terminal](https://github.com/zephexMCP/zephex-web-terminal) | Same Mode 2 **in the browser** |
| [agent-skills](https://github.com/zephexMCP/agent-skills) | Installable agent skill |

Product: [zephex.dev](https://zephex.dev) · Docs: [zephex.dev/docs](https://zephex.dev/docs) · X: [@zephex_dev](https://x.com/zephex_dev)

---

<p align="center">
  <b>Same tools. Your terminal. Your cwd.</b><br/>
  <code>curl -fsSL https://zephex.dev/cli/install.sh | bash</code>
</p>
