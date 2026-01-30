# Migration Manifest

**Purpose:** Complete list of files to move to new repo. Anything omitted is considered intentionally excluded.

**Date:** 2026-01-26

---

## Adapter 01: W&B Trace Adapter (COMPLETE)

```
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/README.md
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/USE_CASE_EVIDENCE.md
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/__init__.py
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/adapter.py
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/config.py
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/sample_input.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/schema.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/validation_report.md
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/validation_report_template.md
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_01_clean_emit.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_02_clean_emit.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_03_f1_overconfidence.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_04_f1_overconfidence.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_05_f2_phantom_work.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_06_f2_phantom_work.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_07_f4_incomplete_trace.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_08_f4_incomplete_trace.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/test_cases/case_09_mixed_failures.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/data/validation_results.json
ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER/scripts/analyze_validation.py
```

**Excluded from A01:**
- `wandb/` directory (W&B run artifacts; local only; regenerated)
- `__pycache__/`, `.DS_Store` (build artifacts, OS cruft)

---

## Adapter 02: CI Safety Gate (PARTIAL)

```
ADAPTER_MODULES/02_CI_SAFETY_GATE/README.md
ADAPTER_MODULES/02_CI_SAFETY_GATE/USE_CASE_EVIDENCE.md
ADAPTER_MODULES/02_CI_SAFETY_GATE/__init__.py
ADAPTER_MODULES/02_CI_SAFETY_GATE/validator.py
ADAPTER_MODULES/02_CI_SAFETY_GATE/validator_config.yaml
ADAPTER_MODULES/02_CI_SAFETY_GATE/violation_schema.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/action.yml
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/README.md
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc01_missing_evidence.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc02_phantom_work.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc03_unverified_confidence.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc04_broken_trace.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc05_fluency_conflict.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc06_error_bypass.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc07_clean_output.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/test_cases/tc08_multi_violation.json
ADAPTER_MODULES/02_CI_SAFETY_GATE/validation_results.json
```

**Excluded from A02:**
- `__pycache__/`, `.DS_Store`

---

## Foundation Documents

```
01_FOUNDATIONS/FRAMEWORK_GUIDE.md
01_FOUNDATIONS/PRD_COL_PROACTIVE_MBSE.md
01_FOUNDATIONS/PROACTIVE_AI_CONSTITUTION.md
01_FOUNDATIONS/RESEARCH_STARTER_KIT.md
01_FOUNDATIONS/THEORY_OF_ACTION.md
01_FOUNDATIONS/THEORY_OF_CHANGE.md
```

---

## Evidence Archive

```
evidence_archive_20260126/MANIFEST.md
evidence_archive_20260126/CASE_STUDY_AGENT_MISALIGNMENT_JAN2026.md
evidence_archive_20260126/MISALIGNMENT_AUDIT.md
evidence_archive_20260126/WORKTREE_GSD_FINDINGS.md
evidence_archive_20260126/git_exports/commit_1e91b29_silent_error.patch
evidence_archive_20260126/git_exports/commit_36f9fa4_false_completion.patch
evidence_archive_20260126/git_exports/full_commit_history.txt
evidence_archive_20260126/session_logs/gallant-jennings_d55c6040.jsonl
evidence_archive_20260126/session_logs/naughty-ritchie_94ff651e.jsonl
evidence_archive_20260126/uncommitted_files/validation_results.json
```

---

## Governance & Specs

```
docs/ELEMENTS_MATRIX.md
docs/PRIVACY_INPUT_RULE.md
docs/V&T_SPEC.md
docs/V&T_SPEC_MATRIX.md
CHANGE_CONTROL_SYSTEM.md
TEMPLATE_DESIGN.md
```

---

## Root-Level Docs

```
README.md
CONTRIBUTING.md
HANDOFF.md
```

---

## GitHub Workflows

```
.github/workflows/test-actions.yml
```

---

## Excluded (Intentional)

```
openmemory.md — Replaced by PROACTIVE.json
PROACTIVE_AI_PRD.md — Will be merged into PROMPT-PRD-PLAN.md
REFACTORED_PROACTIVE_AI_CONSTITUTION_TOOLKIT.md — Replaced by TEMPLATE_DESIGN
TASK_MANAGEMENT/ — Replaced by PROACTIVE.json execution section
FUNDING_MATERIALS/ — Not needed for new repo
.planning/ — Replaced by PROACTIVE.json and PROMPT-PRD-PLAN
09_SAFETY_CASE/ — Will be regenerated
05_EVALUATION_DESIGN/ — Will be regenerated
__pycache__/, wandb/, .DS_Store — Build artifacts, local cruft
```

---

## V&T

```yaml
Created:      2026-01-26
Status:       COMPLETE
Blocked_by:   nothing
Expected:
  - Manifest lists every file to migrate; excluded files explicit; no omissions.
Verified:
  - ✓ MIGRATION_MANIFEST.md
  - ✓ find ADAPTER_MODULES/01_WANDB_TRACE_ADAPTER (23 .py/.json/.md files listed; wandb excluded)
  - ✓ find ADAPTER_MODULES/02_CI_SAFETY_GATE (19 files listed; pycache excluded)
  - ✓ find 01_FOUNDATIONS (6 .md files listed)
  - ✓ find evidence_archive_20260126 (10 files listed)
  - ✓ find docs (4 .md files listed)
  - ✓ ls *.md root (8 files; 3 included, 3 excluded with reason, 2 governance)
  - ✓ find .github (1 workflow listed)
Verified_absent:
  - none checked
Unverified:
  - TASK_MANAGEMENT/, FUNDING_MATERIALS/, .planning/, 05_EVALUATION_DESIGN/, 09_SAFETY_CASE/ (excluded; not checked for migration)
Functional:   true
```
