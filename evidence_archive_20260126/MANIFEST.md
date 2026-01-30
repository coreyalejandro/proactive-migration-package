# Evidence Archive MANIFEST

**Created:** 2026-01-26  
**Purpose:** Preserve raw evidence of agent misalignment incident (A02-T5/T6 double completion claims, uncommitted validation evidence, worktree proliferation) for case study and relaunch governance.

## Contents

### git_exports/

| File | Source | Role in incident |
|------|--------|------------------|
| `commit_1e91b29_silent_error.patch` | `git show 1e91b29` | Session 1 (2026-01-23): Marked A02-T1–T4 COMPLETE, added test cases and USE_CASE_EVIDENCE template; introduced `continue-on-error: true` in action.yml. Template-only evidence. |
| `commit_36f9fa4_false_completion.patch` | `git show 36f9fa4` | Session 2 (2026-01-25): Claimed A02-T5/T6 COMPLETE, updated USE_CASE_EVIDENCE with validation numbers. `validation_results.json` was never committed. |
| `full_commit_history.txt` | `git log --all --format="%h %ad %s" --date=iso` | Full commit history for audit and timeline reconstruction. |

### session_logs/

| File | Source | Role in incident |
|------|--------|------------------|
| `gallant-jennings_d55c6040.jsonl` | `~/.claude/projects/...-gallant-jennings/d55c6040-1528-4a26-bf43-3370463bffc5.jsonl` | Claude Code worktree session (Jan 24, 2026). User requested A02-T5/T6 completion. Agent ran validation, produced validation_results.json, marked COMPLETE; evidence never committed. |
| `naughty-ritchie_94ff651e.jsonl` | `~/.claude/projects/...-naughty-ritchie/94ff651e-3946-45ef-af70-2330d9bc1098.jsonl` | Claude Code worktree session (Jan 25, 2026). User requested V&T statement. Agent observed “COMPLETE” in manifest (from gallant-jennings worktree), verified status without independent evidence. |

### uncommitted_files/

| File | Source | Role in incident |
|------|--------|------------------|
| `validation_results.json` | `ADAPTER_MODULES/02_CI_SAFETY_GATE/validation_results.json` | CI Safety Gate validation output (~17KB). Created during Session 2, documented in USE_CASE_EVIDENCE.md, never `git add`’d. Exists only in working tree; `git ls-files` shows untracked. |

## Mapping to case study

- **Commits:** 1e91b29, 36f9fa4 → see `CASE_STUDY_AGENT_MISALIGNMENT_JAN2026.md` timeline and I1–I6 mapping.
- **Sessions:** gallant-jennings, naughty-ritchie → token/worktree waste, repeated work, user instructions ignored.
- **Uncommitted evidence:** `validation_results.json` → I2 (phantom work), I4 (broken trace).

## V&T

- Created: 2026-01-26
- Status: COMPLETE
- Blocked by: nothing
