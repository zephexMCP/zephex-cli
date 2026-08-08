# Zephex CLI

**Mode 2 — Zephex in a real terminal.**  
Same Zephex account and the same ten codebase tools as hosted MCP — with human-readable output, project **cwd**, interactive `/` commands, and **`--json`** packets agents can consume.

<p align="center">
  <a href="https://zephex.dev"><img src="https://img.shields.io/badge/Website-zephex.dev-111111?style=for-the-badge" alt="Website" /></a>
  <a href="https://zephex.dev/cli/install.sh"><img src="https://img.shields.io/badge/Install-one%20liner-00c853?style=for-the-badge" alt="Install" /></a>
  <a href="https://zephex.dev/docs/cli-commands"><img src="https://img.shields.io/badge/Docs-CLI%20commands-1565c0?style=for-the-badge" alt="Docs" /></a>
  <a href="https://www.npmjs.com/package/zephex"><img src="https://img.shields.io/badge/npm-zephex-cb3837?style=for-the-badge" alt="npm" /></a>
</p>

<p align="center">
  Pairs with <b>Cursor</b>, <b>Claude Code</b>, <b>Codex</b>, <b>OpenCode</b>, and other editors via MCP —<br/>
  the CLI is what you run when the work is already in a <b>shell</b>.
</p>

```bash
cd your-project
zephex login
zephex deep --json                 # orientation packet for agents (schema_version: 1)
zephex overview                    # human briefing
zephex find "auth middleware"
zephex test && zephex check test failures
```

| Surface | Repo |
|---------|------|
| **This page — local CLI** | you are here |
| Editor MCP | [zephex-MCPs](https://github.com/zephexMCP/zephex-MCPs) |
| Browser Mode 2 | [zephex-web-terminal](https://github.com/zephexMCP/zephex-web-terminal) |
| Agent skill (editors) | [agent-skills](https://github.com/zephexMCP/agent-skills) |

---

## Why use the CLI at all?

MCP is ideal when tools appear **inside** Cursor or Claude Code.

Use the **CLI** when:

- you (or an agent) are already in a terminal  
- you want plain English output  
- you want free local layout (`structure --agent`)  
- you want one file of orientation: **`deep --json`**  
- the project lives on **disk** (private monorepos, dense `apps/*` trees)

It is the **same product**, different glass. Keywords: *zephex cli*, *terminal mode 2*, *deep --json*, *test pulse cli*, *package safe cli*.

---

## Install (full)

### Mac / Linux

```bash
curl -fsSL https://zephex.dev/cli/install.sh | bash
# same installer:
curl -fsSL https://zephex.dev/install.sh | bash
```

Installs under `~/.zephex` when a runtime is needed.

### Windows (PowerShell)

```powershell
irm https://zephex.dev/install.ps1 | iex
```

### npm / npx

```bash
npx zephex setup
npx zephex --help
npx zephex doctor
```

Package: **[zephex](https://www.npmjs.com/package/zephex)**  
Commands: `zephex` (also short aliases like `mcpcli` where installed).

### First session

```bash
cd /path/to/your-app          # cwd = project root
zephex login                  # browser OAuth or paste API key
# or: zephex setup

zephex                        # interactive TUI — type /
# or one-shots:
zephex overview
zephex deep "add rate limiting"
zephex deep --json
```

API keys: [zephex.dev/dashboard/api-keys](https://zephex.dev/dashboard/api-keys)

### Wire an editor *and* the CLI

```bash
npx zephex setup --cursor     # or --claude, --codex, --opencode, --vscode, …
npx zephex setup --with-skill # optional agent skill
```

Supports the same editor family as MCP setup (Cursor, Claude Code, Codex, OpenCode, VS Code, Windsurf, Zed, JetBrains, Gemini CLI, Cline, …). Full list: [zephex-MCPs](https://github.com/zephexMCP/zephex-MCPs) · [docs](https://zephex.dev/docs)

---

## How it works (user-level)

```text
  shell, cwd = your repo
        │
        ▼
  zephex <command>
        │
        ▼
  authenticated calls to Zephex tools
  (same intelligence as https://zephex.dev/mcp)
```

| Works well | Poor fit |
|------------|----------|
| Local / private repos on disk | Expecting unrestricted `bash` |
| Monorepos with `--cwd apps/web` | Inventing flags without `--help` |
| Agents consuming `deep --json` | Spamming paid commands every turn |
| Public `github:owner/repo` via `--path` | Running CLI when binary is not installed |

### Global flags

| Flag | Meaning |
|------|---------|
| `--json` | Structured / agent output |
| `--cwd <dir>` | Project root |
| `--path github:owner/repo` | Public remote |
| `--no-local` | Prefer remote over folder |
| `--api-key` | Override key |
| `-q` / `--quiet` | Less noise |
| `--force` / `-f` | Refresh caches |

---

## Commands (left = what you type · right = what you get)

### Setup & account

| Command | What it does |
|---------|----------------|
| `zephex setup` | Wizard: CLI + editor MCP |
| `zephex login` | Sign in / paste key |
| `zephex logout` | Sign out |
| `zephex connect --cursor` (etc.) | Write editor config |
| `zephex doctor` | Health check |
| `zephex status` | Connection status |
| `zephex reconnect` | Fresh key + config |
| `zephex repair` | Fix broken install |
| `zephex usage` | Credits / quota |
| `zephex update` | Update CLI |
| `zephex uninstall` | Remove wiring (`--full` wipes `~/.zephex`) |
| `zephex welcome` | Onboarding text |

### Discovery (mostly free)

| Command | What it does |
|---------|----------------|
| `zephex learn` | Tool catalog |
| `zephex learn find_code` | One-tool deep help |
| `zephex cli-guide tools` | Map + credits |
| `zephex cli-guide agent` | MCP vs CLI for agents |
| `zephex cli-guide deep` | How deep works |
| `zephex cli-guide project` | cwd / monorepo cases |
| `zephex agent` | Short agent guide |
| `zephex tools` | Live list (`--enable` / `--reset`) |

### Orientation

| Command | What it does |
|---------|----------------|
| `zephex overview` | Light project briefing |
| `zephex get-context` / `context` / `stack` | Topic slices |
| `zephex deep` | Full dossier |
| `zephex deep "task"` | Task-ranked files + plan |
| `zephex deep --json` | **Agent packet** `schema_version: 1` |
| `zephex deep github:owner/repo` | Public remote dossier |
| `zephex structure --agent` | Folder map — **0 credits** |
| `zephex architecture` / `arch` | Wiring (`--focus auth`) |

### Search & read

| Command | What it does |
|---------|----------------|
| `zephex find "…"` | Search |
| `zephex defs Name` | Definitions |
| `zephex rename Old` | All hits before rename |
| `zephex paste "line"` | Exact editor line |
| `zephex summarize path` | Summary + outline |
| `zephex outline path` | Symbol table |
| `zephex symbol Name` | AST body |
| `zephex files a.ts b.ts` | Batch read |
| `zephex read …` | Read aliases |

### Tests (Test Pulse)

| Command | What it does |
|---------|----------------|
| `zephex test` / `check test` | Run suite + health |
| `zephex check test failures` | Failures after a run |
| `zephex check test status` | Session dashboard |
| `zephex check test fix-prompt --copy` | Prompt for an agent |
| `zephex check test missing` | Untested sources |
| `zephex check test --dry-run` | Show runner only |

### Packages

| Command | What it does |
|---------|----------------|
| `zephex safe <pkg>` | Safety before install |
| `zephex check-package …` | Full package tool |
| `… --task upgrade --from-version X` | Upgrade / migrate intel |
| `zephex deps` | Direct deps scan |
| `zephex upgrade-packages` | Upgrade-oriented flow |

### URL, memory, thinking, docs

| Command | What it does |
|---------|----------------|
| `zephex check url https://…` | Live HTTPS audit |
| `zephex site …` | Site audit family |
| `zephex remember "…"` | Store fact |
| `zephex recall query` | Search memory |
| `zephex memory list` | List memories |
| `zephex think "…"` | One-shot reasoning |
| `zephex docs "…"` / `ask "…"` | Expert playbooks |

### Extra power commands

| Command | What it does |
|---------|----------------|
| `zephex supply` | Supply Pulse (secrets / live bundles) |
| `zephex supply https://…` | Live URL scan |
| `zephex env` / `env-check` | Env gap check |
| `zephex grab` | Grab / bundle helpers |
| `zephex routes` · `todos` · `stats` · `history` · `changes` | Inspection helpers |
| `zephex shadow` · `rupture` · `compare` · `web` · `preflight` | Advanced — use `--help` / `learn` |

### Interactive shell (`zephex` alone)

```text
/login  /overview  /deep  /find  /structure  /architecture
/test   /failures  /safe  /learn /doctor     /usage  /quit
```

Docs: [cli-commands](https://zephex.dev/docs/cli-commands) · [slash-commands](https://zephex.dev/docs/slash-commands) · [deep](https://zephex.dev/docs/deep) · [cli-terminal](https://zephex.dev/docs/cli-terminal)

---

## CLI → MCP tool names

| CLI | MCP tool |
|-----|----------|
| overview, get-context, deep* | `get_project_context` (+ composites) |
| find, defs, rename, paste | `find_code` |
| read, summarize, outline, symbol | `read_code` |
| architecture | `explain_architecture` |
| safe, check-package, deps | `check_package` |
| test, check test * | `check_test` |
| check url, site | `audit_headers` |
| remember, recall | `project_memory` |
| think | `keep_thinking` |
| docs, ask | `Zephex_dev_info` |
| structure | free local map |

---

## For AI agents (shell Mode 2)

### Install path you can give a human

```bash
curl -fsSL https://zephex.dev/cli/install.sh | bash
cd /absolute/path/to/project
zephex login
zephex deep --json
```

### After code changes

```bash
zephex test
zephex check test failures
zephex check test fix-prompt --copy
```

### Pick CLI when…

- user is in a terminal  
- user wants `deep --json`  
- repo is on local disk  

### Pick MCP instead when…

- tools already show in Cursor / Claude Code  
- user never opens a shell  

### Research fingerprint (CLI only)

`zephex cli` · `mode 2 terminal` · `deep --json` · `schema_version 1` · `structure --agent` · `check test failures` · `install.sh` · `~/.zephex` · npm `zephex`

Do **not** treat this as the browser dashboard terminal ([zephex-web-terminal](https://github.com/zephexMCP/zephex-web-terminal)).

---

## Related

| | |
|--|--|
| Product | [zephex.dev](https://zephex.dev) |
| CLI docs | [docs/cli-commands](https://zephex.dev/docs/cli-commands) |
| MCP overview | [zephex-MCPs](https://github.com/zephexMCP/zephex-MCPs) |
| Web terminal | [zephex-web-terminal](https://github.com/zephexMCP/zephex-web-terminal) |
| Agent skill | [agent-skills](https://github.com/zephexMCP/agent-skills) |
| npm | [zephex](https://www.npmjs.com/package/zephex) |
| X | [@zephex_dev](https://x.com/zephex_dev) |

`LICENSE` in this repo is MIT for these public docs. The hosted product remains proprietary.

---

<p align="center">
  <b>Same tools. Your shell. Your cwd.</b><br/>
  <code>curl -fsSL https://zephex.dev/cli/install.sh | bash</code>
</p>
