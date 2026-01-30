# Change Control System

**Requirement:** All changes tracked in real time. Nothing committed without visual inspection. Diff as file mirror. Max 2 concurrent changes; rest queued FIFO. Zero-shot exempt configurable.

**Rule:** No agent may ever control the change-control mechanism. Install, configure, run, disable, or hide it—human only. If an agent controls it, the agent can turn it off or bypass it without telling anyone.

**Zero-shot install:** During fail-test phases, the human approves. Not the agent. Human-in-the-loop at each fail phase.

---

## Components

### 1. File watcher

- **Tool:** `fswatch` (macOS) / `inotifywait` (Linux) / `chokidar` (Node).
- On change: diff, notification, approval prompt. Revert if rejected.

### 2. Queue

- `max_concurrent: 2`. FIFO. Emit file, type, timestamp, queue position.

### 3. Pre-commit

- Final gate. Full diff, approve/reject. Block commit on reject.

### 4. Config

```yaml
# .proactive/change-control.yaml
change_control:
  enabled: true
  max_concurrent: 2
  require_approval: true
  notification: { desktop: true, terminal: true }
  diff_display: { method: "terminal" | "ide" | "desktop", always_visible: true }
  queue: { fifo: true, show_status: true }
  zero_shot_exempt: false
```

---

## V&T

```yaml
Created:      2026-01-26
Status:       DESIGN
Blocked_by:   implementation
Expected:
  - Watcher detects changes; diff + notification; approve/revert.
  - Max 2 active; overflow queued FIFO; status visible.
  - Pre-commit shows diff; blocks commit until approval.
  - Zero-shot exempt configurable; when true, skip queue only; still approve.
  - Change-control is human-only; no agent control ever.
  - Zero-shot install: human approves during fail-test phases.
Verified:
  - ✓ CHANGE_CONTROL_SYSTEM.md
  - ✓ docs/V&T_SPEC.md
Verified_absent:
  - none checked
Unverified:
  - .proactive/watch-changes.sh
  - .proactive/queue-manager.py
  - .proactive/change-control.yaml
  - fswatch on target env
  - inotify on target env
  - chokidar on target env
Functional:   false
```
