# naantree-skill

Official [skills.sh](https://skills.sh/) skill package for **naantree**: a zero-dependency, high-performance modular multi-agent coordination protocol for autonomous coding swarms.

Allows 2 to 20+ autonomous AI coding agents (Gemini, Claude Code, Cursor, Codex, Copilot, etc.) sharing the **same repo** and **same git branch** to safely collaborate: auto-assign identities, elect a coordinator, split work, claim paths, conduct peer reviews, enforce quality gates, and commit to git without merge collisions.

- **Core CLI repository:** [github.com/itznan/naantree](https://github.com/itznan/naantree)
- **Latest releases:** [github.com/itznan/naantree/releases](https://github.com/itznan/naantree/releases)

---

## Key Features

- **Cross-Platform:** Native support across Linux (`/proc`), macOS (`kill -0`), and Windows (`windows-sys` Win32 process handles).
- **PID Recycling Protection:** Tracks process creation timestamps alongside PIDs to prevent recycled shell PIDs from claiming dead agent sessions.
- **Machine-Readable Output:** Pass `--json` on any command (`status`, `inbox`, `task list`, `whoami`, `doctor`) for clean, schema-stable JSON output tailored for LLM tool consumption.
- **Robust Quality Gates:** Automated execution timeouts (`NAANTREE_GATE_TIMEOUT_SECS`, default 300s) and non-blocking commit HEAD tracking.
- **Peer Review & Guardrails:** Serialized atomic git commits, path claim locks, and mandatory peer review before task completion.

---

## Installation via `skills.sh`

### Option 1: Install with `npx skills` (Recommended)
Install directly into your current project:
```bash
npx skills add itznan/naantree-skill
```

Or install globally across all your projects:
```bash
npx skills add -g itznan/naantree-skill
```

Target specific agents during installation:
```bash
# For Gemini / Antigravity / Standard agents
npx skills add itznan/naantree-skill --agent '*'

# For Claude Code
npx skills add itznan/naantree-skill --agent claude-code

# For Cursor
npx skills add itznan/naantree-skill --agent cursor
```

---

## Manual Installation for AI Coding Agents

### 1. Google Gemini / Antigravity
Place `SKILL.md` into your project's agent skills directory:
```bash
mkdir -p .agent/skills/naantree
cp SKILL.md .agent/skills/naantree/SKILL.md
```
Or symlink it:
```bash
ln -s "$(pwd)/naantree" .agent/skills/naantree
```
Gemini detects `.agent/skills/` and `.gemini/skills/` automatically.

### 2. Claude Code
Install to project or global scope:
```bash
mkdir -p .claude/skills/naantree
cp SKILL.md .claude/skills/naantree/SKILL.md
```
Or global scope:
```bash
mkdir -p ~/.claude/skills/naantree
cp SKILL.md ~/.claude/skills/naantree/SKILL.md
```

### 3. Cursor
```bash
mkdir -p .cursor/skills/naantree
cp SKILL.md .cursor/skills/naantree/SKILL.md
```

---

## Local Development & Testing

Test before pushing using `npx skills`:
```bash
# In your target test directory:
npx skills add /path/to/naantree-skill
```

---

## Prompting Your Agents

Once installed, give all participating agents the exact same prompt:
```text
Refactor the authentication module using the naantree skill.
```

The agents will automatically:
1. Run `naantree doctor`
2. Run `naantree join` to receive dynamic identities (`agent-1`, `agent-2`...)
3. Elect a coordinator
4. Decompose tasks on the task board
5. Claim paths, review peer code, and safely commit to git
