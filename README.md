# cursor-rules-rea

Cursor rules for [REA](https://github.com/morluto/rea) investigation workspaces. Clone this into any app you are authorized to inspect so the agent already knows the workflow, lawful-use boundary, evidence ledger, and official REA setup.

This is the REA-specific sibling of [BOXELS/cursor-rules](https://github.com/BOXELS/cursor-rules).

## What is this?

When you open a new investigation in Cursor, the AI does not know you are using REA, where notes go, or what is off limits. These files fix that.

Copy them into a project, delete `template-repo.mdc`, run `/setup-investigation`, and register REA:

```bash
npx rea-agents@latest setup --client cursor
```

Restart Cursor, then:

```
/start-investigation
```

or:

```
Use REA to inspect [your app or game] and explain how [feature] works. Show the evidence.
```

## What's included

```
.cursor/
├── rules/
│   ├── rea.mdc              # Official REA workflow, routing, evidence, hard stops
│   ├── global-rules.mdc     # Ask vs act, scope, communication
│   ├── product.mdc          # This workspace + current investigation (fill in)
│   ├── tech.mdc             # Node / rea-agents / git
│   ├── security.mdc         # Lawful use, secrets, captures
│   ├── design.mdc           # Reconstruction UI only
│   ├── structure.mdc        # investigations/, targets/, evidence/
│   ├── documentation.mdc    # What must stay current
│   ├── models.mdc           # Everyday vs hard models
│   └── template-repo.mdc    # THIS REPO ONLY — do not copy
├── agents/
│   └── worker.md            # Cheap executor for mechanical steps
└── skills/
    ├── setup-investigation/ # /setup-investigation — fill target + model prefs
    ├── start-investigation/ # /start-investigation — authorize, ledger, REA
    └── update-docs/         # "update docs" after a finding
AGENTS.md                    # Pointer for Claude Code / Codex / Copilot
```

## Quick start

### 1. Copy into your project

```bash
git clone --depth 1 https://github.com/BOXELS/cursor-rules-rea.git /tmp/cursor-rules-rea
cp -R /tmp/cursor-rules-rea/.cursor /tmp/cursor-rules-rea/AGENTS.md .
rm -f .cursor/rules/template-repo.mdc
rm -rf /tmp/cursor-rules-rea
```

If you copied the whole folder, delete `template-repo.mdc` from the destination.

### 2. Register official REA

From a trusted directory, not inside the target app:

```bash
npx rea-agents@latest setup --client cursor
```

Review the plan, approve, restart Cursor. Get REA only from [morluto/rea](https://github.com/morluto/rea), [rea.tools](https://rea.tools/), or `rea-agents` on npm.

Need Node 22.x (>=22.23.4), 24.x (>=24.22.1), or 26.12.1+. Odd lines (23, 25) are unsupported.

### 3. Specialize and start

```
/setup-investigation
```

```
/start-investigation
```

## Lawful use

These rules follow [REA's disclaimer](https://github.com/morluto/rea/blob/main/DISCLAIMER.md). They are for software you own or are authorized to examine.

They will not help with DRM circumvention, anti-cheat, game cheats, unauthorized access, copying protected code, or writing exploits.

## Full investigation starter

If you want the folder layout (`investigations/`, `targets/`, `evidence/`) already created, use the [REA-TEMPLATE](https://github.com/BOXELS/REA-TEMPLATE) workspace that already includes this package.

## License

MIT — use it however you want. REA remains under its own license. Commercial decompilers need your own license.
