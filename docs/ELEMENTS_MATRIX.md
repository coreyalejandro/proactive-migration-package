# Elements Matrix

**Verified:** A check was run (`test -f`, `which`) and the result recorded. Yes or No.

**Path:** Only if the file exists and has content. Otherwise —.

| Element | Verified | Path |
|---------|----------|------|
| .proactive/watch-changes.sh | Yes | — |
| .proactive/queue-manager.py | Yes | — |
| .proactive/change-control.yaml | Yes | — |
| fswatch on target environment | Yes | /opt/homebrew/bin/fswatch |
| inotify on target environment | Yes | — |
| chokidar on target environment | Yes | — |
| editor configuration on user machine | No | — |
| tooling configuration on user machine | No | — |

**Checks run:** `test -f` for .proactive/* (all missing). `which fswatch` → found; `which inotifywait` → not found; `which chokidar` → not found. No check for editor or tooling config.
