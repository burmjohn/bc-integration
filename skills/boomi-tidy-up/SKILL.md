---
name: boomi-tidy-up
description: Clean generated Boomi active-development artifacts while preserving workspace directory structure and .gitkeep files. Use when a user wants to reset local Boomi development artifacts after review, testing, or before starting another Boomi integration workspace task.
---

# Boomi Tidy Up

Use this skill to clean generated Boomi development artifacts from a project
workspace while preserving the expected folder structure.

## What to clean

- Files under `active-development/*/`
- Files under `active-development/.sync-state/`
- Files under `active-development/feedback/`

## What to preserve

- `.gitkeep` files
- `.env` and `.env.local`
- `preferred_connections.md`
- User files outside `active-development/`

## Command

Run from the project workspace root:

```bash
find active-development -type f ! -name ".gitkeep" -delete 2>/dev/null || true
```

After running, report that generated artifacts were removed and the directory
structure was preserved.
