# Agent instructions

Project conventions for AI coding agents live in `.cursor/rules/*.mdc` and `.cursor/skills/*/SKILL.md`. Cursor loads them automatically. If you are a different agent (Claude Code, Codex, Copilot, etc.), read these before making changes:

If `.cursor/rules/template-repo.mdc` exists, read it first — you are in the cursor-rules-rea template repository, not an investigation. That file is not part of the copy set.

- `.cursor/rules/rea.mdc` — when to use official REA, routing, evidence, hard stops
- `.cursor/rules/global-rules.mdc` — how to behave: ask vs. act, scope discipline
- `.cursor/rules/product.mdc` — what this workspace is and the current investigation
- `.cursor/rules/tech.mdc` — Node/REA stack, CLI, git rules
- `.cursor/rules/security.mdc` — lawful use, secrets, captures
- `.cursor/rules/structure.mdc` — where investigation files go
- `.cursor/rules/documentation.mdc` — doc location and what to keep current
- `.cursor/rules/design.mdc` — UI standards (only when touching reconstructions)
- `.cursor/rules/models.mdc` — Cursor model guidance; safe to skip outside Cursor

Workflows:

- `.cursor/skills/start-investigation/SKILL.md` — begin a lawful REA investigation
- `.cursor/skills/setup-investigation/SKILL.md` — fill investigation-specific placeholders
- `.cursor/skills/update-docs/SKILL.md` — persist findings into notes and rules

Subagent: `.cursor/agents/worker.md` — low-cost executor for fully specified steps (Cursor only).

Don't duplicate rule content here. This file is intentionally a pointer.
