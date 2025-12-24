# Documentation Authority Audit Report

**Date:** 2024-12-24  
**Scope:** TheraPrac workspace (api, web, infra)  
**Auditor:** AI Documentation Audit

---

## Executive Summary

Completed documentation authority audit across the TheraPrac workspace. Primary finding: **significant documentation duplication in the API project** where backend standards are repeated across 4+ documents. Created explicit authority indexes (`docs/_index.md`) for each project and streamlined `.cursorrules` files to focus on authority rather than restating standards.

---

## Changes Made

### 1. Created Authority Index Files

| File | Purpose |
|------|---------|
| `theraprac-api/docs/_index.md` | Establishes canonical, design, informational, and historical document categories |
| `theraprac-web/docs/_index.md` | Establishes document authority hierarchy for frontend |
| `theraprac-infra/docs/_index.md` | Establishes document authority for infrastructure |

### 2. Updated .cursorrules Files

| File | Changes |
|------|---------|
| `theraprac-api/.cursorrules` | Removed restated handler patterns; now points to canonical docs |
| `theraprac-web/.cursorrules` | Streamlined to focus on authority and prohibitions |

---

## Document Authority Summary

### theraprac-api

| Authority | Documents |
|-----------|-----------|
| **CANONICAL** | `api/openapi/api.yaml`, `docs/BACKEND_STANDARDS.md`, `docs/BUILD_*.md` |
| **DESIGN** | `docs/compliance/*`, `docs/recurring-appointments/*`, `docs/intake/*` |
| **INFORMATIONAL** | `docs/BACKEND_QUICK_REFERENCE.md`, most `docs/guides/*` |
| **DEPRECATED** | `docs/BACKEND_ARCHITECTURE_GUIDE.md`, `docs/guides/backend-standards.md` |
| **HISTORICAL** | `docs/archived/*`, `docs/phase*.md` files |

### theraprac-web

| Authority | Documents |
|-----------|-----------|
| **CANONICAL** | `docs/FRONTEND_ARCHITECTURE_GUIDE.md`, `docs/reference/*`, `docs/BUILD_*.md` |
| **DESIGN** | `docs/architecture/*`, `docs/features/*`, `docs/intake/*` |
| **INFORMATIONAL** | `docs/guides/*`, `docs/getting-started/*` |
| **HISTORICAL** | `docs/archive/*`, `docs/migration/*` |

### theraprac-infra

| Authority | Documents |
|-----------|-----------|
| **CANONICAL** | `README.md`, `docs/DEPLOYMENT_WORKFLOW.md`, `docs/ZITI_*.md` |
| **INFORMATIONAL** | Other docs in `docs/` |

---

## Items Requiring Follow-Up (Not Implemented)

### 1. Duplicate Documents to Delete or Merge

**Action Required:** These documents contain nearly identical content and should be consolidated:

| Document | Recommendation |
|----------|---------------|
| `theraprac-api/docs/BACKEND_ARCHITECTURE_GUIDE.md` | Delete (duplicate of `BACKEND_STANDARDS.md`) |
| `theraprac-api/docs/guides/backend-standards.md` | Delete (duplicate of `BACKEND_STANDARDS.md`) |

### 2. Historical Documents to Archive

**Action Required:** Move these to `docs/archived/`:

- `theraprac-api/docs/phase1-execution-checklist.md`
- `theraprac-api/docs/phase2-execution-checklist.md`
- `theraprac-api/docs/phase3-*.md`
- `theraprac-api/docs/phase3.5-*.md`
- `theraprac-api/docs/phase4.0-*.md`
- `theraprac-api/docs/phase4.1-*.md`

### 3. Pre-Commit Hook Optimization

**Finding:** The API pre-commit hook runs the full test suite (including integration tests), which may cause friction and `--no-verify` usage.

**Recommendation (not implemented):**

| Check | Pre-Commit | CI |
|-------|------------|-----|
| Lint | ✅ | ✅ |
| Type/Build check | ✅ | ✅ |
| Unit tests | ✅ | ✅ |
| Integration tests | ❌ | ✅ |
| Full test suite | ❌ | ✅ |

The web project already follows this pattern (see `docs/PRE_COMMIT_HOOKS.md`).

### 4. Missing .cursorrules

**Finding:** `theraprac-infra` has no `.cursorrules` file.

**Recommendation:** Not required for simpler infrastructure project, but could add minimal one if AI assistance is frequently used.

---

## Authority Conflict Resolution

When documents conflict, resolution order:

### API
1. `api/openapi/api.yaml` wins for API behavior
2. `docs/BACKEND_STANDARDS.md` wins for handler patterns
3. `docs/BUILD_STANDARDS.md` wins for versioning

### Web
1. `docs/FRONTEND_ARCHITECTURE_GUIDE.md` wins for component patterns
2. `docs/reference/design-system.md` wins for visual design
3. `docs/reference/rbac/api-reference.md` wins for permissions

### Infra
1. `docs/DEPLOYMENT_WORKFLOW.md` wins for deployment
2. Script `--help` output takes precedence over stale docs

---

## Verification

To verify this audit:

1. **Authority indexes exist:**
   ```bash
   ls theraprac-api/docs/_index.md
   ls theraprac-web/docs/_index.md
   ls theraprac-infra/docs/_index.md
   ```

2. **Cursorrules are minimal:**
   - Should NOT contain handler code templates
   - Should NOT contain error handling examples
   - Should ONLY contain authority references and prohibitions

3. **Duplicates are marked:**
   - `theraprac-api/docs/_index.md` lists deprecated documents

---

## Maintenance

### When Adding Documentation

1. Check `docs/_index.md` for existing authority
2. Add new canonical docs to the index
3. Do NOT create documents that duplicate existing canonical content

### When Documents Conflict

1. Consult `docs/_index.md` for authority hierarchy
2. The higher-authority document wins
3. Update or delete the lower-authority document

---

**Report Complete**

