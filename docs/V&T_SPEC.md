# V&T Spec

**Schema:** `v&t-v1`  
**Rule:** V&T is the sole deliverable after task completion. No summary, no chat. As rigid as code.

**No [].** Empty lists are forbidden. Explicit enumeration every time. Using `[]` to mean "nothing unverified" or "nothing missing" without listing what was checked is deception.

---

## Required Fields

```yaml
Created:       ISO8601
Status:        NOT_STARTED | IN_PROGRESS | COMPLETE | BLOCKED
Blocked_by:    "nothing" | list of IDs or deps
Expected:      # Stated beforehand. No inference.
  - outcome_1
  - outcome_2
Verified:      # Explicit list. Every item we relied on, checked. ✓ per item.
  - ✓ path/to/thing_a
  - ✓ path/to/thing_b
Verified_absent:  # Explicit list. Every item we verified is missing.
  - path/we/checked/not_there
Unverified:    # Explicit list. Every item we did NOT check.
  - thing_we_did_not_verify
Functional:    true | false
```

---

## Constraints

- **Expected:** Must be declared before work. Nothing listed that was not stated upfront.
- **Verified:** List each artifact/fact we checked. Each gets ✓. Every time. No omission.
- **Verified_absent:** List each we verified is missing. If we checked nothing absent, say so in a single explicit line—e.g. `Verified_absent: [none checked]`—and ensure Verified enumerates what we did check.
- **Unverified:** List each we did not check. If we verified everything we relied on, Unverified lists only what we explicitly skipped. Never use `[]` to imply "all good."
- **Functional:** true iff all Expected hold, no Blocked_by, and Verified/Unverified are fully enumerated.

---

## Example

```yaml
Created:       2026-01-26T00:00:00Z
Status:        COMPLETE
Blocked_by:    nothing
Expected:
  - File watcher runs; diff on change; approve/revert.
  - Max 2 concurrent; queue FIFO.
Verified:
  - ✓ .proactive/watch-changes.sh
  - ✓ .proactive/change-control.yaml
Verified_absent:
  - .proactive/queue-manager.py
Unverified:
  - fswatch on user machine
Functional:    true
```
