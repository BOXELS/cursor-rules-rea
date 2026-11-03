# Clone cursor-rules-rea into any REA app

The portable rules package lives at [BOXELS/cursor-rules-rea](https://github.com/BOXELS/cursor-rules-rea). Use it when you already have a project (or a fresh investigation folder) and want the same REA Cursor setup.

## Copy into an existing repo

```bash
git clone --depth 1 https://github.com/BOXELS/cursor-rules-rea.git /tmp/cursor-rules-rea
cp -R /tmp/cursor-rules-rea/.cursor /tmp/cursor-rules-rea/AGENTS.md .
rm -f .cursor/rules/template-repo.mdc
rm -rf /tmp/cursor-rules-rea
```

Then in Cursor:

```
/setup-investigation
```

And register REA if this machine has not already:

```bash
npx rea-agents@latest setup --client cursor
```

Restart Cursor after setup.

## What not to copy

- `template-repo.mdc` — that file is only for the published template repo
- Do not overwrite an existing `.cursor/` without checking for project-specific rules you want to keep
