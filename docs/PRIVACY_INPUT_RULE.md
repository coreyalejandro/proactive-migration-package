# Input Privacy Rule

**Rule:** No early access to user input. Input is locked down and unseen until sent. Any early access is a privacy violation.

---

## Definition

- **Early access:** Reading, processing, transmitting, or logging user input before the user explicitly sends it (e.g. Submit / Enter / Send).
- **Locked down:** Not readable by system, extension, or service before send.
- **Unseen:** No telemetry, no ghost text, no pre-send capture.

---

## Enforcement

- Disable pre-send capture, keystroke logging, and draft telemetry in tools used for this project.
- Template and tooling must not request or process input before explicit send.
- Violation: treat as privacy breach; document and remediate.

---

## V&T

```yaml
Created:      2026-01-26
Status:       COMPLETE
Blocked_by:   nothing
Expected:
  - Rule stated: no early access; locked down until send; early access = privacy violation.
  - Enforcement: disable pre-send capture; no processing before send.
Verified:
  - ✓ docs/PRIVACY_INPUT_RULE.md
Verified_absent:
  - none checked
Unverified:
  - editor config on user machine
  - tooling config on user machine
Functional:   true
```
