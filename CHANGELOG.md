# Changelog

All notable changes to `naantree-skill` will be documented in this file.

## [Unreleased] - 2026-10-11

### Changed
- **Skill Rewrite**:
  - START section instructs agents to trust the role printed by `join` rather than guessing or assuming agent-1 is coordinator.
  - Instructions to always pass `--as agent-N` explicitly to survive fresh subshells.
  - Workers instructed to run `naantree coordinator claim` when no coordinator is alive.
  - Added explicit anti-patterns: never inspect process trees (`ps`/`pstree`), never inspect other agents' internal transcript/state files, never resume unassigned IDs.
  - Added ready-to-paste user-prompt template that does not hardcode roles or IDs.
