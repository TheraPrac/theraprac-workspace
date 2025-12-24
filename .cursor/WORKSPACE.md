# TheraPrac Workspace

This workspace contains three projects that together form the TheraPrac platform.

---

## Projects

| Project | Purpose | Authority Index |
|---------|---------|-----------------|
| `theraprac-api` | Go backend API | `docs/_index.md` |
| `theraprac-web` | Next.js frontend | `docs/_index.md` |
| `theraprac-infra` | Terraform/Ansible infrastructure | `docs/_index.md` |

Each project's `docs/_index.md` is the authoritative map for that project's documentation. Consult it to understand what documents are canonical, what are design, and what are historical.

---

## How Documentation Authority Works

1. **Canonical documents define behavior.** Implementation must conform to them.
2. **Design documents propose behavior.** They are not authoritative until implemented.
3. **Informational documents assist.** They may become stale; verify against canonical sources.
4. **Historical documents record.** They explain past decisions but do not govern current work.

When documents conflict, consult the project's `docs/_index.md` for resolution order.

---

## How Changes Are Made Safely

This workspace follows a **design-first, documentation-locked** workflow:

1. **Understand before changing.** Read the relevant canonical documents.
2. **Design before implementing.** For non-trivial changes, update or create design documents first.
3. **Implement to specification.** Code must match the design and canonical patterns.
4. **Validate before committing.** Pre-commit hooks exist to catch errors early.
5. **Document completion.** When a subsystem is complete, its design documents become canonical or historical.

---

## Pre-Commit Hooks Are Not Optional

Pre-commit hooks are intentional safety nets. They exist to:
- Catch errors before they enter the repository
- Enforce coding standards consistently
- Validate that tests pass

**Using `--no-verify` is not an acceptable workflow.**

If a hook fails:
- The failure must be investigated
- The underlying issue must be fixed
- The commit must succeed through normal hook execution

Bypassing hooks does not make problems disappear. It moves them downstream where they are harder to fix.

---

## What "DONE" Means for a Subsystem

A subsystem is complete when:

1. **Design documents are fulfilled.** All specified behavior is implemented.
2. **Canonical documents are updated.** The implementation patterns are documented.
3. **Tests pass.** All hooks and CI checks succeed.
4. **Design documents are reclassified.** They become canonical (if they define ongoing behavior) or historical (if they only record the implementation journey).

---

## Reference Example: Intake

The **Intake** subsystem is a closed, canonical example of a complete subsystem.

- **API:** `theraprac-api/docs/intake/` — schema, state machine, versioning strategy
- **Web:** `theraprac-web/docs/intake/` — implementation readiness, decisions, gaps

When implementing new subsystems, follow the Intake pattern:
- Comprehensive design documents before implementation
- Clear state machine and schema definitions
- Explicit gap analysis and decision records
- Reclassification to canonical or historical when complete

---

## If You Feel Lost

1. **Start with the project's `docs/_index.md`.** It tells you what documents are authoritative.
2. **Read canonical documents first.** They define how things work.
3. **Check design documents for context.** They explain intent for in-progress work.
4. **Do not invent behavior.** If something is unclear, ask rather than guess.
5. **Do not bypass safety checks.** If hooks fail, fix the failure.

When uncertain, prefer restraint over invention.

---

## Project Entry Points

| Project | README | Docs Index |
|---------|--------|------------|
| API | `theraprac-api/README.md` | `theraprac-api/docs/_index.md` |
| Web | `theraprac-web/README.md` | `theraprac-web/docs/_index.md` |
| Infra | `theraprac-infra/README.md` | `theraprac-infra/docs/_index.md` |

---

**This document is the workspace entry point. It does not restate standards. It points to them.**

