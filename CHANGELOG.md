# Changelog

All notable changes to `naantree-skill` will be documented in this file.

## [Unreleased] - 2026-10-11

### Added
- **Machine-Readable JSON Mode**: Added guidance for agents to use `--json` (e.g., `nt --json status`, `nt --as agent-N --json inbox`, `nt --as agent-N --json task list`) for reliable schema parsing.
- **Cross-Platform Support & PID Recycling Protection**: Updated skill to note native Windows (`windows-sys`), macOS, and Linux support, with PID session files validated against process creation timestamps.
- **Quality Gate Timeouts & Non-blocking HEAD Drift**: Documented gate execution timeout (`NAANTREE_GATE_TIMEOUT_SECS`, default 300s) and non-blocking gate result persistence across concurrent commits.

### Changed
- **Skill Rewrite**:
  - START section instructs agents to trust the role printed by `join` rather than guessing or assuming agent-1 is coordinator.
  - Instructions to always pass `--as agent-N` explicitly to survive fresh subshells.
  - Workers instructed to run `naantree coordinator claim` when no coordinator is alive.
  - Added explicit anti-patterns: never inspect process trees (`ps`/`pstree`), never inspect other agents' internal transcript/state files, never resume unassigned IDs.
  - Added ready-to-paste user-prompt template that does not hardcode roles or IDs.
  - Synchronized nested `naantree/SKILL.md` and root `SKILL.md`.
