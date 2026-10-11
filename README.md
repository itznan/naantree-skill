# naantree-skill

Official [skills.sh](https://skills.sh/) skill package for **naantree**: a zero-dependency, high-performance modular multi-agent coordination protocol.

Allows 2 to 20+ autonomous AI coding agents (Gemini, Claude Code, Cursor, Copilot, etc.) sharing the **same repo** and **same git branch** to self-organize: auto-assign identities, elect a coordinator, split work, claim paths, conduct peer reviews, and safely commit without git collisions.

Core CLI repository: [github.com/itznan/naantree](https://github.com/itznan/naantree)

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

## How to Add to Gemini & AI Coding Agents

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
```
"Refactor the authentication module using the naantree skill."
```

The agents will automatically:
1. Run `naantree doctor`
2. Run `naantree join` to receive dynamic identities (`agent-1`, `agent-2`...)
3. Elect a coordinator
4. Decompose tasks on the task board
5. Claim paths, review peer code, and safely commit to git
