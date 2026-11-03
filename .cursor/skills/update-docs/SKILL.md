---
name: update-docs
description: Bring investigation notes and .cursor/rules back in sync after a finding, reconstruction, or convention change. Use when the user says "update docs", "update documentation", "sync docs", or after an investigation milestone.
---

# Update Docs

Run this whenever the user asks to update documentation, or after a change other agents will need. Do all five steps before reporting back. Do not ask which files to touch — find them.

Read `.cursor/rules/documentation.mdc` first if you haven't this session.

## Workflow

```
- [ ] 1. Find related docs
- [ ] 2. Update existing docs in place
- [ ] 3. Create a new doc only if none covers the area
- [ ] 4. Cross-reference from .cursor/rules/
- [ ] 5. Report every file touched
```

### 1. Find related docs

Search `docs/` and `investigations/` for the target name, feature, Evidence IDs, and reconstruction folder. Read headers and update every file that mentions the affected area.

### 2. Update existing docs in place

Edit, don't append. Remove stale conclusions. Prefer editing an existing ledger over creating a duplicate investigation folder.

### 3. Create a new doc only when none exists

Only if no existing file covers the area. Follow naming in `documentation.mdc`. Document only what was actually found or implemented.

### 4. Cross-reference from `.cursor/rules/`

- Cross-cutting → `global-rules.mdc`.
- REA workflow → `rea.mdc`.
- Domain-specific → `tech.mdc`, `security.mdc`, `structure.mdc`, `models.mdc`, or a new focused `.mdc`.
- Add a one-line "see `docs/FOO.md`" or `investigations/<slug>/FINDINGS.md` pointer when a longer reference exists.

### 5. Report

End with a one-line list of every doc and rule file edited or created.

## Do not

- Ask "which docs should I update?"
- Invent findings or document intent that wasn't observed.
- Leave old and new conclusions both described as current.
- Commit raw captures or secrets while updating docs.
