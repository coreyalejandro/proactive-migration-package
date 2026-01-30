# PROACTIVE Repo Template

**Purpose:** GitHub template. Governance, CI Safety Gate, structure from day one.

---

## Structure

```
proactive-template/
├── PROACTIVE.json
├── PROMPT-PRD-PLAN.md
├── README.md
├── .github/workflows/proactive-gate.yml
├── .github/PULL_REQUEST_TEMPLATE.md
├── .proactive/
│   ├── validator_config.yaml
│   ├── pre-commit-hook.sh
│   ├── governance-rules.md
│   └── change-control.yaml
├── adapters/_template/
│   ├── README.md, validator.py, adapter.py
│   ├── test_cases/tc01_example.json
│   ├── USE_CASE_EVIDENCE.md
│   └── validator_config.yaml
├── evidence/README.md
├── docs/constitution.md, governance.md, blind-mans-test.md
└── scripts/
    ├── validate-evidence.sh
    ├── update-proactive-json.sh
    └── check-completion-claims.sh
```

---

## Governance (baked in)

- Pre-commit: no "COMPLETE" without evidence; PROACTIVE.json sync; no worktree branches.
- CI: proactive-gate on every push; scan COMPLETE/SHIPPED; block `continue-on-error: true`; run I1–I6 validator.
- PROACTIVE.json: single source of truth. PROMPT-PRD-PLAN: governing prompt + PRD + plan + invariant enforcement.
- **Input privacy:** No early access to user input. Locked down, unseen until sent. Early access = privacy violation. See `docs/PRIVACY_INPUT_RULE.md`.
- **Change-control:** Human-only. No agent may control, disable, or hide it. See `CHANGE_CONTROL_SYSTEM.md`.

---

## V&T

```yaml
Created:      2026-01-26
Status:       DESIGN
Blocked_by:   change-control implementation; user install of non-negotiables
Expected:
  - Repo created from template; placeholders filled; governance active.
  - CI Safety Gate runs on push; pre-commit runs on commit.
  - Evidence folder; adapter _template; validator config present.
Verified:
  - ✓ TEMPLATE_DESIGN.md
  - ✓ docs/V&T_SPEC.md
  - ✓ docs/PRIVACY_INPUT_RULE.md
Verified_absent:
  - none checked
Unverified:
  - proactive-template/ tree
  - PROACTIVE.json
  - proactive-gate.yml
  - GitHub template workflow
Functional:   false
```
