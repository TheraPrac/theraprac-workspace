# Documentation Spine Audit Report

**Date:** 2024-12-24  
**Scope:** theraprac-api, theraprac-web, theraprac-infra

---

## Summary

This audit established a clear documentation spine across the TheraPrac workspace:

```
WORKSPACE.md
    ↓
Project docs/_index.md (per project)
    ↓
Authoritative documents (per topic)
```

---

## Authoritative Documents Per Project

### theraprac-api

| Topic | Authoritative Document |
|-------|------------------------|
| API contract | `api/openapi/api.yaml` |
| Coding patterns | `docs/BACKEND_STANDARDS.md` |
| Build/deploy | `docs/BUILD_AND_DEPLOY.md` |
| Versioning | `docs/BUILD_STANDARDS.md` |
| Validation | `docs/guides/api-validation-guide.md` |
| Error handling | `docs/guides/error-handling-guide.md` |
| Intake design | `docs/intake/*` (10 documents, design complete) |

### theraprac-web

| Topic | Authoritative Document |
|-------|------------------------|
| Architecture | `docs/FRONTEND_ARCHITECTURE_GUIDE.md` |
| Build/deploy | `docs/BUILD_AND_DEPLOY.md` |
| Versioning | `docs/BUILD_STANDARDS.md` |
| Pre-commit | `docs/PRE_COMMIT_HOOKS.md` |
| Security | `docs/SECURITY.md` |
| Testing strategy | `docs/TEST_COVERAGE_STRATEGY.md` |
| Design system | `docs/reference/design-system.md` |
| RBAC | `docs/reference/rbac/api-reference.md` |
| Auth architecture | `docs/reference/auth-architecture.md` |
| Components | `docs/reference/components/*` |
| Data model | `docs/reference/data-model/*` |

### theraprac-infra

| Topic | Authoritative Document |
|-------|------------------------|
| Project overview | `README.md` |
| Deployment | `docs/DEPLOYMENT_WORKFLOW.md` |
| Ziti operations | `docs/ZITI_RESOURCE_MANAGEMENT.md` |
| Ziti access control | `docs/ZITI_ROLES_AND_POLICIES.md` |

---

## Documents Demoted to Historical/Deprecated

### theraprac-api

| Document | Reason | Superseded By |
|----------|--------|---------------|
| `docs/BACKEND_ARCHITECTURE_GUIDE.md` | Duplicate content | `BACKEND_STANDARDS.md` |
| `docs/guides/backend-standards.md` | Duplicate content | `BACKEND_STANDARDS.md` |
| `docs/architecture/backend-guardrails.md` | Overlapping content | `BACKEND_STANDARDS.md` + `.cursorrules` |
| `docs/phase*.md` (12 files) | Completed phase work | HISTORICAL |

### theraprac-web

| Document | Reason |
|----------|--------|
| `docs/archive/*` | Implementation summaries |
| `docs/migration/*` | Completed migration planning |

---

## Authority Collisions Resolved

### theraprac-api: Backend Standards

**Collision:** Three documents covered backend coding patterns:
- `BACKEND_STANDARDS.md`
- `BACKEND_ARCHITECTURE_GUIDE.md`
- `guides/backend-standards.md`

**Resolution:** `BACKEND_STANDARDS.md` is authoritative. Others are deprecated and should be deleted.

### theraprac-api: Backend Guardrails

**Collision:** `architecture/backend-guardrails.md` overlaps with `BACKEND_STANDARDS.md` and `.cursorrules`.

**Resolution:** Content is covered elsewhere. Document is deprecated.

---

## Missing Documents Added to Indexes

### theraprac-web

Documents that existed but were not listed in `_index.md`:
- `SECURITY.md` — added as AUTHORITATIVE
- `TEST_COVERAGE_STRATEGY.md` — added as AUTHORITATIVE
- `reference/auth-architecture.md` — added as AUTHORITATIVE

### theraprac-api

Documents that existed but were not listed in `_index.md`:
- `BACKEND_COMPLIANCE_PLAN.md` — added as SUPPORTING
- `BUILD_DEPLOY_OPTIMIZATION.md` — added as SUPPORTING
- `architecture/backend-guardrails.md` — added as DEPRECATED

---

## DONE Markers Applied

### theraprac-api: Intake Subsystem

**Status:** Design documentation complete. Implementation in progress.

The Intake subsystem has comprehensive design documentation across 10 documents covering:
- Database schema and data model
- State machine and transitions
- Versioning strategy
- Assignment workflows
- Client and staff UX specifications
- File storage and audit logging

This documentation is marked as design-complete in `docs/_index.md`.

---

## No-Verify Enforcement

Documented in:
- `theraprac-workspace/.cursor/WORKSPACE.md` — workspace-level directive
- `theraprac-api/.cursorrules` — Commit Discipline section
- `theraprac-web/.cursorrules` — Commit Discipline section
- `theraprac-infra/.cursorrules` — Commit Discipline section

All documents state:
- Pre-commit hooks are mandatory
- `--no-verify` is not acceptable
- Hook failures must be fixed, not bypassed

---

## Remaining Ambiguity

### Files Marked for Deletion

The following files are deprecated and should be deleted:
- `theraprac-api/docs/BACKEND_ARCHITECTURE_GUIDE.md`
- `theraprac-api/docs/guides/backend-standards.md`
- `theraprac-api/docs/architecture/backend-guardrails.md`

**Action:** These deletions are documented but not executed by this audit.

### Phase Documents

12 phase execution documents in `theraprac-api/docs/` are marked HISTORICAL but remain in the main `docs/` directory rather than `docs/archived/`.

**Action:** Consider moving to `archived/` for clarity.

---

## Audit Complete

The documentation spine is now established:
- Each project has a `docs/_index.md` with explicit authority classifications
- `WORKSPACE.md` provides workspace-level navigation
- Authority collisions are resolved and documented
- No-verify enforcement is documented at all levels

---

**Auditor:** AI Assistant  
**Date:** 2024-12-24

