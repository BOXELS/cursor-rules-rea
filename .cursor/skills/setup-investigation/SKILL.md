---
name: setup-investigation
description: Fill investigation-specific placeholders in product.mdc, models.mdc, and global-rules.mdc. Use when the user runs /setup-investigation or /setup-rules on a fresh copy of cursor-rules-rea.
disable-model-invocation: true
---

# Setup Investigation

Fill the investigation-specific placeholders. Do not weaken `rea.mdc` or `security.mdc`. The user may not be technical: explain in plain language and never assume they know REA, Hopper, or Ghidra.

Start by switching to Plan mode if available.

## Shipped files you may edit

Fill **only** these, in this order:

1. `product.mdc` — Current investigation section
2. `models.mdc` — This project's setup
3. `global-rules.mdc` — Role / "I am" line only if the user wants a different working style

Optionally set the `model:` line in `.cursor/agents/worker.md` during step 2.

Do not edit `rea.mdc`, `security.mdc`, `tech.mdc`, `structure.mdc`, `documentation.mdc`, or `design.mdc` unless the user explicitly asks. Those are REA defaults.

## Step 0 — `template-repo.mdc`

If `.cursor/rules/template-repo.mdc` exists, stop and ask:

> This folder still has `template-repo.mdc`, which belongs only to the cursor-rules-rea template repository. Are you (A) maintaining the template — I'll stop — or (B) starting a real investigation from a clone — I'll delete `template-repo.mdc` and continue?

- **A:** Stop.
- **B:** Delete `.cursor/rules/template-repo.mdc`, then continue.

## Step 1 — Detect

Look at the project root (ignore `.cursor/`, `.git/`, `AGENTS.md`, `README.md`, `LICENSE`, `docs/`, empty `targets/` / `investigations/_template/`).

- Empty investigation workspace → interview below.
- Existing investigation notes or a `reconstructions/` app → inspect first, confirm second.

Never modify target binaries or reconstruction app code during setup. You only write the files listed above.

## Order and what to ask

### 1. `product.mdc`

- What are you investigating? Name, type (desktop app, game, JS/Electron, APK, website, binary).
- Do you own it, or do you have written authorization? If no, stop. Do not set up an unauthorized target.
- Absolute path or install name. If unknown, leave `[not set]` and tell them to drop it in `targets/`.
- Primary question (one sentence). Out of scope stays the security list already in the file.
- Show a short summary. Write only after they confirm.

### 2. `models.mdc`

- Cursor plan (Hobby / Pro / Pro+ / Ultra / Teams). Cost vs quality. Privacy Mode.
- Recommend one everyday model and one hard-task model. Default everyday: Grok 4.7. Default hard: Opus 5 thinking.
- If they have a cheap high-allowance model, set worker `model:` to that ID. If not, set `inherit` and say delegation is off.
- Keep the two tier tables and plan-then-delegate section.

### 3. `global-rules.mdc`

- Experience level and ask-first vs act-first.
- Only change the Role / "I am" lines. Leave REA and security behavior intact.

## Finish

- Confirm no `[bracketed placeholders]` remain in the files you edited.
- Tell the user they can start inspecting with `/start-investigation` (or "Use REA to inspect …"). If REA is not connected, offer to run `npx rea-agents@latest setup --client cursor` and ask them to restart Cursor. This repo is the only template.
