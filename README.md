# cursor-rules-rea

A starter template for [Cursor's](https://cursor.com) `.cursor/` folder, meant to use official [REA](https://github.com/morluto/rea) (Reverse Engineer Anything). Same idea as [BOXELS/cursor-rules](https://github.com/BOXELS/cursor-rules): copy it into a project, and the AI already knows the workflow. This one is for inspecting software you own (or are allowed to examine), not for building a product from scratch.

You do not need a second repo. **This is the only template.**

## What is this?

When you open Cursor to inspect an app or game, the AI does not know you are using REA, where notes go, or what is off limits. These files fix that.

You do not have to fill them in yourself. Open the folder in Cursor and type `/setup-investigation` (or `/start-investigation` if you already know what to inspect).

- **New folder** — create an empty project, drop this template in, tell the AI what you want to inspect.
- **Existing project** — drop the files into the repo you already have. Setup does not edit your app code; it only fills the rule files.

REA itself is not inside this repo. The first time you inspect something, the agent (or you) runs official setup so this computer gets current REA. Restart Cursor when asked. Run the same setup later if you want a newer REA.

## Start (non-coders)

1. On GitHub, open [BOXELS/cursor-rules-rea](https://github.com/BOXELS/cursor-rules-rea) and click **Use this template**. Name the new repo after what you want to inspect.
2. In Cursor, clone that new repo (welcome screen **Clone repo**, or **File → Open Folder**).
3. In chat, type `/start-investigation` and say what you want to inspect.

The agent asks whether you are allowed to examine it, then does the rest.

Or say:

```
Use REA to inspect [my app or game] and explain how [feature] works. Show the evidence.
```

## What's included

```
.cursor/
├── rules/
│   ├── rea.mdc                 # Official REA workflow, evidence, hard stops
│   ├── global-rules.mdc        # Ask vs act, how to talk to you
│   ├── product.mdc             # This investigation (filled by /setup-investigation)
│   ├── tech.mdc                # Node / REA / git
│   ├── security.mdc            # Lawful use, secrets, captures
│   ├── design.mdc              # Only if we build a reconstruction UI
│   ├── structure.mdc           # Where notes and reconstructions go
│   ├── documentation.mdc       # What must stay current
│   ├── models.mdc              # Everyday vs hard models
│   └── template-repo.mdc       # THIS REPO ONLY — do not copy
├── agents/
│   └── worker.md               # Cheap helper for mechanical edits
└── skills/
    ├── setup-investigation/    # /setup-investigation — fill the placeholders
    ├── start-investigation/    # /start-investigation — authorize and inspect
    └── update-docs/            # "update docs" after a finding
AGENTS.md
docs/                           # Start here + authorization
investigations/_template/       # Note files the agent copies for each target
```

> **Why `.mdc`?** Cursor only loads `.mdc` files in `.cursor/rules/`. Keep that extension.

**Rules vs skills:** a *rule* is always on; a *skill* is a procedure you trigger (`/start-investigation`).

`template-repo.mdc` belongs only in this GitHub repo. If you copy the whole folder, delete that file (or `/setup-investigation` will ask).

## Copy into an existing project

Copy into the project root:

- everything in `.cursor/rules/` except `template-repo.mdc`
- `.cursor/skills/`
- `.cursor/agents/worker.md`
- `.claude/agents/` (Claude Code subagents)
- `AGENTS.md`
- `docs/` and `investigations/_template/` if you want the note folders too

## Get current REA

This template does not ship REA. After you copy it (or when the agent says REA is not connected):

```bash
npx rea-agents@latest setup --client cursor
```

Restart Cursor. That is how you get current REA. Re-run the same command later to refresh. Get REA only from [morluto/rea](https://github.com/morluto/rea), [rea.tools](https://rea.tools/), or `rea-agents` on npm.

Need Node 22.x (>=22.23.4), 24.x (>=24.22.1), or 26.12.1+. Odd versions (23, 25) are unsupported.

## Lawful use

[REA's disclaimer](https://github.com/morluto/rea/blob/main/DISCLAIMER.md): software you own or are authorized to examine. This template will not help with DRM, license bypass, anti-cheat, game cheats, unauthorized access, or writing exploits.

See [docs/AUTHORIZATION.md](docs/AUTHORIZATION.md).

## Maintaining this repository

This GitHub repo publishes the template. `template-repo.mdc` is always-on here so agents do not treat *this* folder as an investigation.

- Leave shipped rules as the template. Edit them only to change what copiers get.
- Do not run `/start-investigation` against a real target in this repo.
- After a change that affects how copies are used, update this README in the same change.

## License

MIT. REA has its own license. Commercial decompilers need your own license.
