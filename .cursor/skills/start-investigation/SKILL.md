---
name: start-investigation
description: Start a lawful REA investigation. Ask for the target and authorization, create investigation notes, then inspect with official REA. Use when the user runs /start-investigation or says "use REA to inspect" / "start a REA investigation".
---

# Start Investigation

Run this when the user wants to inspect a chosen app, game, binary, or site with official REA.

## 1. Identify the target

If they did not name a target and path, ask **one** question: what should we inspect, and where is it?

Do not pick an example app for them. Paths in old notes or fixtures are not the target.

## 2. Authorization gate

Ask how they are authorized (own it, employer artifact, written permission, CTF they are allowed to play). Read `docs/AUTHORIZATION.md`.

Stop if the request is DRM circumvention, anti-cheat, game cheats, unauthorized access, license bypass, copying protected code, or exploit/PoC writing. Do not continue with "high-level tips" that still get them there.

## 3. Open the ledger

If `investigations/_template/` exists, copy it to `investigations/<slug>/`. If it does not, create `investigations/<slug>/` with `TARGET.md`, `QUESTIONS.md`, `EVIDENCE.md`, `FINDINGS.md`, and `NOTES.md` using the headings in this template's copies under `investigations/_template/` when present, or the same five-file layout described in `structure.mdc`. Fill `TARGET.md` and `QUESTIONS.md` before calling REA.

Update the "Current investigation" block in `.cursor/rules/product.mdc` to match.

## 4. Use official REA

- If REA MCP tools are available, use them. Follow `.cursor/rules/rea.mdc` and the installed `reverse-engineer-anything` skill if present.
- If tools are missing, say so. Suggest restarting Cursor, then `npx rea-agents@latest setup --client cursor` from a trusted directory outside the target. For a JS/Electron tree you may fall back to:

```bash
npx -y rea-agents@latest analyze-javascript-application /absolute/path/to/app --json
```

- Start with the advertised tool that matches the target. Summary-first. Cite Evidence IDs in `EVIDENCE.md`.
- Do not repeat an identical call. Do not install cracked native engines.

## 5. Report

Write `FINDINGS.md` in plain language: observations vs inferences vs unknowns. If they asked to build a similar feature, implement it in `reconstructions/` from observed behavior — do not paste protected code.

Example operator prompt after setup:

> Use REA to inspect [target] and explain how [feature] works. Show the evidence.
