# TheraPrac Workspace Documentation Spine

This document is the single entry point for the TheraPrac multi-project workspace.

---

## Projects

| Project | Purpose | Documentation Index |
|---------|---------|---------------------|
| `theraprac-api` | Go backend API | `theraprac-api/docs/_index.md` |
| `theraprac-web` | Next.js frontend | `theraprac-web/docs/_index.md` |
| `theraprac-infra` | Terraform/Ansible infrastructure | `theraprac-infra/docs/_index.md` |

Each project's `docs/_index.md` is the authoritative map for that project's documentation.

---

## How Documentation Authority Works

```
WORKSPACE.md (this file)
    ↓
Project docs/_index.md
    ↓
Authoritative documents (per topic)
```

**Authority Levels:**

| Level | Meaning |
|-------|---------|
| **AUTHORITATIVE** | Source of truth. Implementation must conform. |
| **SUPPORTING** | Explanatory guides. May become stale; verify against authoritative. |
| **HISTORICAL** | Archived context. Do not use for implementation decisions. |

When documents conflict, consult the project's `docs/_index.md` for resolution order.

---

## Pre-Commit Hooks Are Not Optional

Pre-commit hooks are intentional safety nets. They exist to:
- Catch errors before they enter the repository
- Enforce coding standards consistently
- Validate that tests pass

**Using `--no-verify` is not an acceptable workflow.**

If a hook fails:
1. The failure must be investigated
2. The underlying issue must be fixed
3. The commit must succeed through normal hook execution

Bypassing hooks does not make problems disappear. It moves them downstream where they are harder to fix.

Any commit using `--no-verify` is treated as a **process failure**, not a workaround.

---

## Project Entry Points

| Project | README | Docs Index |
|---------|--------|------------|
| API | `theraprac-api/README.md` | `theraprac-api/docs/_index.md` |
| Web | `theraprac-web/README.md` | `theraprac-web/docs/_index.md` |
| Infra | `theraprac-infra/README.md` | `theraprac-infra/docs/_index.md` |

---

## If You Feel Lost

1. **Start with the project's `docs/_index.md`.** It tells you what documents are authoritative.
2. **Read authoritative documents first.** They define how things work.
3. **Check supporting documents for context.** They explain intent.
4. **Do not invent behavior.** If something is unclear, ask rather than guess.
5. **Do not bypass safety checks.** If hooks fail, fix the failure.

---

**This document is navigation and discipline only. It does not restate standards.**

