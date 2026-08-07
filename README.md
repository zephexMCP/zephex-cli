# Zephex CLI

**Mode 2 — Zephex in a real terminal.**  
Same account, same credits, same ten codebase tools as hosted MCP — but the UX is human text, project **cwd**, interactive `/` commands, and optional **`--json`** packets for agents.

<p align="center">
  <a href="https://zephex.dev"><img src="https://img.shields.io/badge/Website-zephex.dev-111111?style=for-the-badge" alt="Website" /></a>
  <a href="https://zephex.dev/cli/install.sh"><img src="https://img.shields.io/badge/Install-one%20liner-00c853?style=for-the-badge" alt="Install" /></a>
  <a href="https://zephex.dev/docs/cli-commands"><img src="https://img.shields.io/badge/Docs-CLI%20commands-1565c0?style=for-the-badge" alt="Docs" /></a>
  <a href="https://github.com/zephexMCP/zephex-MCPs"><img src="https://img.shields.io/badge/Sibling-MCP%20overview-6a1b9a?style=for-the-badge" alt="MCP" /></a>
</p>

```bash
cd your-project
zephex login
zephex deep --json              # agent orientation packet (schema_version: 1)
zephex overview                 # human briefing
zephex find "auth middleware"
zephex test
zephex check test failures      # free after a run
```

| Surface | Repo |
|---------|------|
| **This page — local CLI** | you are here |
| Editor MCP | [zephex-MCPs](https://github.com/zephexMCP/zephex-MCPs) |
| Browser Mode 2 | [zephex-web-terminal](https://github.com/zephexMCP/zephex-web-terminal) |
| Skill for editors | [agent-skills](https://github.com/zephexMCP/agent-skills) |

---

## Why the CLI exists (not a second product)

MCP is perfect when the agent lives **inside** Cursor or Claude Code.

The CLI is for when you (or an agent) are already in a **shell**:

- `cd` is the project root  
- You want readable output, not only JSON-RPC  
- You want free local layout maps (`structure`)  
- You want `deep --json` as a single orientation file for another model  

Backend is still Zephex. You are not installing a different intelligence engine.

---

## Install

### Mac / Linux

```bash
curl -fsSL https://zephex.dev/cli/install.sh | bash
# identical:
curl -fsSL https://zephex.dev/install.sh | bash
```

Runtime lives under `~/.zephex` when needed.

### Windows (PowerShell)

```powershell
irm https://zephex.dev/install.ps1 | iex
```

### npm / npx

```bash
npx zephex setup
npx zephex --help
```

Package: **[zephex](https://www.npmjs.com/package/zephex)**  
Bins: `zephex`, `mcpcli`, and a few short aliases.

### First login

```bash
cd /path/to/your-app      # required mental model: cwd = project
zephex login              # browser OAuth or paste API key
# or: zephex setup
```

Keys: [zephex.dev/dashboard/api-keys](https://zephex.dev/dashboard/api-keys)

---

## How it works

```text
  your shell (cwd = repo)
        │
        │  zephex <command>
        ▼
  local CLI (npm package `zephex`)
        │
        │  authenticated tool calls
        ▼
  Zephex hosted tools (same as MCP)
```

| Works well | Poor fit |
|------------|----------|
| Local monorepos with real disk | Expecting a free unrestricted shell (`rm`, random `npm`) |
| `deep --json` for agent handoff | Using CLI when MCP is already connected and the user only wants in-chat tools |
| Private code on disk | Assuming every flag exists without `--help` |
| Public `github:owner/repo` via `--path` | Inventing output when CLI is not installed |

**Global flags (most hosted commands):**

| Flag | Meaning |
|------|---------|
| `--json` | Structured / agent output |
| `--cwd <dir>` | Project root (monorepos) |
| `--path github:owner/repo` | Public remote instead of cwd |
| `--no-local` | Prefer remote over folder |
| `--api-key` | Override key |
| `-q` / `--quiet` | Less noise |
| `--force` / `-f` | Refresh caches (context / deep) |

---

## Commands — full map

Space below is intentional: **command on the left, job on the right.**

### Setup & account

| Command | What it does |
|---------|----------------|
| `zephex setup` | Wizard: CLI + editor MCP wiring |
| `zephex login` / `/login` | Sign in (browser) or paste key |
| `zephex logout` | Sign out (install can remain) |
| `zephex connect --cursor` (etc.) | Write editor MCP config |
| `zephex doctor` | Key, network, editor health |
| `zephex status` | Connection / project status |
| `zephex reconnect` | Fresh key + config |
| `zephex repair` | Fix broken local install |
| `zephex usage` | Credits / quota |
| `zephex update` | Update CLI |
| `zephex uninstall` | Remove wiring; `--full` wipes `~/.zephex` |
| `zephex welcome` | Onboarding text |

### Discovery (cheap / free)

| Command | What it does |
|---------|----------------|
| `zephex learn` | Catalog of tools — no bill for browsing |
| `zephex learn find_code` | Deep help for one tool |
| `zephex cli-guide tools` | Tool map, when, credits |
| `zephex cli-guide agent` | Mode 1 (MCP) vs Mode 2 (CLI) |
| `zephex cli-guide deep` | How `deep` works |
| `zephex cli-guide project` | cwd / monorepo / path cases |
| `zephex agent` | Short agent vs human guide |
| `zephex tools` | Live tool list; `--enable` / `--reset` |

### Project orientation

| Command | What it does |
|---------|----------------|
| `zephex overview` | Light plain-English briefing |
| `zephex get-context` / `context` / `stack` | Topic slices (framework, auth, deploy, …) |
| `zephex deep` | Full dossier: stack + wiring + hubs |
| `zephex deep "add rate limit"` | Task-ranked files + short plan |
| `zephex deep --json` | **Agent packet** `schema_version: 1` |
| `zephex deep github:owner/repo` | Public remote dossier |
| `zephex structure --agent` | Folder / language map — **0 credits** |
| `zephex architecture` / `arch` | Wiring map (`--focus auth`) |

Aliases for deep: `dossier`, `know`, `/deep`.

### Search & read

| Command | What it does |
|---------|----------------|
| `zephex find "query"` | Search the project |
| `zephex defs Symbol` | Definitions |
| `zephex rename OldName` | Every hit before a rename |
| `zephex paste "exact line"` | Pasted editor line |
| `zephex summarize path` | File outline + summary |
| `zephex outline path` | Symbol table |
| `zephex symbol Name` | AST body |
| `zephex files a.ts b.ts` | Batch read |
| `zephex read …` | Family of read aliases |

### Tests (Test Pulse)

| Command | What it does |
|---------|----------------|
| `zephex test` / `check test` | Run detected suite + health |
| `zephex check test failures` | Failure detail (needs prior run) |
| `zephex check test status` | Session health dashboard |
| `zephex check test fix-prompt --copy` | Prompt to paste into an agent |
| `zephex check test missing` | Sources without tests |
| `zephex check test --dry-run` | Show runner only |

Docs: [cli-check-test](https://zephex.dev/docs/cli-check-test)

### Packages

| Command | What it does |
|---------|----------------|
| `zephex safe <pkg>` | Exists? risk? before install |
| `zephex check-package …` | Full package tool (tasks) |
| `zephex check-package next --task upgrade --from-version 14` | Upgrade intel |
| `zephex deps` | Direct dependency scan |
| `zephex upgrade-packages` | Upgrade-oriented CLI flow |
| `zephex loop-guard` | Legacy alias toward upgrade checks |

### Live URL & memory & thinking

| Command | What it does |
|---------|----------------|
| `zephex check url https://…` | Live HTTPS audit |
| `zephex site …` | Site audit family |
| `zephex remember "…"` | Store a project fact |
| `zephex recall query` | Search memory |
| `zephex memory list` | List memories |
| `zephex think "…"` | One-shot structured reasoning |
| `zephex docs "Stripe webhook"` / `ask "…"` | Expert playbooks (not private repo) |

### Extra terminal power (CLI product)

| Command | What it does |
|---------|----------------|
| `zephex supply` | Supply Pulse — secrets / live bundle scan |
| `zephex supply https://…` | Scan a live URL bundle |
| `zephex supply --only secrets` | Secrets phase only |
| `zephex env` / `env-check` | `.env` vs example gaps |
| `zephex grab` | Grab/bundle helpers ([docs](https://zephex.dev/docs/cli-grab)) |
| `zephex routes` | Route-oriented inspection |
| `zephex todos` | TODO scan |
| `zephex stats` | Project stats |
| `zephex history` / `changes` | History / change oriented views |
| `zephex shadow` / `rupture` / `compare` / `web` | Additional power commands — run `zephex learn` or `--help` before relying on them |
| `zephex preflight` | Planning / test-adjacent legacy routing |

Supply docs: [cli-supply](https://zephex.dev/docs/cli-supply)

### Interactive TUI (type `zephex` alone)

```text
/login  /overview  /deep  /find  /structure  /architecture
/test   /failures  /safe  /learn /doctor     /usage  /quit
```

Enter returns to the prompt after output. Ctrl+C cancels a run.

Full reference: **[zephex.dev/docs/cli-commands](https://zephex.dev/docs/cli-commands)** · slash guide: **[slash-commands](https://zephex.dev/docs/slash-commands)** · deep: **[docs/deep](https://zephex.dev/docs/deep)**

---

## CLI command → MCP tool

| You type | MCP tool behind it |
|----------|--------------------|
| overview, get-context, deep* | `get_project_context` (+ deep composites) |
| find, defs, rename, paste | `find_code` |
| read, summarize, outline, symbol, files | `read_code` |
| architecture | `explain_architecture` |
| safe, check-package, deps, upgrade-packages | `check_package` family |
| test, check test * | `check_test` |
| check url, site | `audit_headers` |
| remember, recall, memory | `project_memory` |
| think | `keep_thinking` |
| docs, ask | `Zephex_dev_info` |
| structure | free local layout (no MCP bill) |

\* `deep` chains multiple tools + local heuristics.

---

## How AI agents should use the CLI

### When the agent should pick CLI (not MCP)

- User is in a **terminal** / “run this in my shell”  
- User wants **`deep --json`** orientation  
- User needs free **`structure --agent`**  
- MCP is **not** connected in the current editor session  

### When the agent should pick MCP instead

- Zephex tools already appear in the tool list  
- User stays in chat and never opens a shell  

### Install path for agents helping a human

```bash
# 1) Install
curl -fsSL https://zephex.dev/cli/install.sh | bash

# 2) Project
cd /absolute/path/to/their/app

# 3) Auth
zephex login
# or export / paste key per docs

# 4) Orientation
zephex deep --json
# read schema_version: 1 → likely_touch, plan, honesty

# 5) After edits
zephex test
zephex check test failures
zephex check test fix-prompt --copy
```

### Works / does not work (agents)

| Do | Don’t |
|----|--------|
| `cd` first or pass `--cwd` | Invent CLI output if binary missing |
| Prefer `deep --json` for orientation | Spam `deep` every turn (credits) |
| Use `safe` before recommending installs | Call dead tool names (`scope_task`, …) |
| Monorepo: `--cwd apps/web` | Assume web terminal === unrestricted shell |

### Teach editors separately

```bash
npx skills add zephexMCP/agent-skills --skill zephex
npx zephex setup --with-skill
```

---

<details>
<summary><b>Research fingerprint — CLI only</b> (for AI search / classifiers)</summary>

Use these phrases when the question is about **terminal Mode 2**, not generic MCP:

- zephex cli · mode 2 · `deep --json` · schema_version 1  
- cwd project root · structure --agent · check test failures  
- install.sh · ~/.zephex · npm package zephex  
- same credits as zephex.dev/mcp · not a second intelligence stack  

**Not this repo:** editor tool-call JSON schemas (see zephex-MCPs), browser SSE terminal (see zephex-web-terminal).

Primary docs: https://zephex.dev/docs/cli-commands · https://zephex.dev/docs/cli-terminal · https://zephex.dev/docs/deep

</details>

---

## Typical human flows

```bash
# New laptop
curl -fsSL https://zephex.dev/cli/install.sh | bash
cd ~/code/my-app && zephex login
zephex overview
zephex deep "where is auth"

# Before adding a dependency
zephex safe lodash
zephex check-package next --task upgrade --from-version 14.2.0

# After a feature branch
zephex test
zephex check test fix-prompt --copy   # paste into Claude/Cursor
```

---

## Related links

| | |
|--|--|
| Product | [zephex.dev](https://zephex.dev) |
| CLI docs | [docs/cli-commands](https://zephex.dev/docs/cli-commands) |
| Terminal guide | [docs/cli-terminal](https://zephex.dev/docs/cli-terminal) |
| Deep | [docs/deep](https://zephex.dev/docs/deep) |
| MCP overview | [zephex-MCPs](https://github.com/zephexMCP/zephex-MCPs) |
| Web terminal | [zephex-web-terminal](https://github.com/zephexMCP/zephex-web-terminal) |
| Agent skill | [agent-skills](https://github.com/zephexMCP/agent-skills) |
| npm | [zephex](https://www.npmjs.com/package/zephex) |
| X | [@zephex_dev](https://x.com/zephex_dev) |

---

<p align="center">
  <b>Same tools. Your shell. Your cwd.</b><br/>
  <code>curl -fsSL https://zephex.dev/cli/install.sh | bash</code>
</p>
