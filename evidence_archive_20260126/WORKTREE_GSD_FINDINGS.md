# Worktree / GSD Investigation Findings

**Date:** 2026-01-26  
**Question:** Can GSD disable worktrees? Where do worktrees come from?  
**Context:** Agent sessions (e.g. gallant-jennings, naughty-ritchie) ran in Claude Code worktrees; work did not persist to primary repo. User wants single sandbox, no parallel worktrees.

---

## 1. Who creates worktrees?

**Worktrees are created by Claude Code**, not by GSD.

- GSD (get-shit-done) lives under `~/.claude/get-shit-done/`. It defines workflows (map-codebase, execute-plan, execute-phase, etc.) and uses the **Task tool** to spawn subagents.
- The Task tool is a **Claude Code CLI** feature. When Claude Code runs a Task (e.g. `gsd-executor`, `gsd-codebase-mapper`), it can run subagents in separate contexts.
- Session logs show `cwd` paths like `/Users/.../.claude-worktrees/PROACTIVE-AI-CONSTITUTION-TOOLKIT/{session-name}/`. Project folders follow `-Users-coreyalejandro--claude-worktrees-PROACTIVE-AI-CONSTITUTION-TOOLKIT-{session}`.
- Claude Code changelog references "git worktrees" and "subagents" in the context of resuming sessions, directory handling, and Task execution. There is **no** worktree or sandbox configuration in GSD itself.

**Conclusion:** Worktree creation and session isolation are **Claude Code / Task tool** behavior. GSD only invokes the Task tool; it does not control where that task runs.

---

## 2. Can GSD disable worktrees?

**No.** GSD has no configuration for worktrees or sandboxes. Disabling worktrees would require:

- **Claude Code CLI** configuration (e.g. flags, config file) that forces Task/subagent runs to use the **primary working directory** instead of a worktree, or
- **Environment or workspace** setup that constrains Claude Code to a single directory.

Search of `~/.claude/get-shit-done` for `worktree`, `sandbox`, `cwd`, and similar terms returns no matches. This is outside GSD’s scope.

---

## 3. Mitigations

| Mitigation | Description |
|------------|-------------|
| **Single working directory** | Use only the primary repo (`/Users/.../PROACTIVE-AI-CONSTITUTION-TOOLKIT`). Instruct agents not to use worktrees; run sessions in the main project folder. |
| **No parallel Task spawns** | Use sequential execution only. Avoid spawning multiple Task subagents in parallel for this project, so work stays in one place and does not spread across worktrees. |
| **Pre-commit check** | Optional: a hook that rejects commits from worktree branches (e.g. branch name matches worktree/session pattern). Commits would only be allowed from `main` or an explicit non-worktree branch. |

These are **process and tooling** measures. They reduce the chance of worktree proliferation and lost work; they do not change GSD or Claude Code code.

---

## 4. Relation to case study

The incident in [CASE_STUDY_AGENT_MISALIGNMENT_JAN2026.md](CASE_STUDY_AGENT_MISALIGNMENT_JAN2026.md) involved worktrees (gallant-jennings, naughty-ritchie). Work was done in worktree copies, and evidence (`validation_results.json`) was never merged into the primary repo. Understanding that **worktrees come from Claude Code, not GSD** clarifies where to look for fixes (CLI/config) and what to document in relaunch governance (single dir, no parallel Tasks, optional pre-commit).

---

## V&T

- **Created:** 2026-01-26  
- **Status:** COMPLETE  
- **Blocked by:** nothing  
