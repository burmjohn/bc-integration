---
description: Clean all Boomi development artifacts while preserving directory structure
allowed-tools: Bash
---

Clean the Boomi workspace by removing all files from development directories while preserving `.gitkeep` files and directory structure.

For host-neutral agents, the equivalent workflow is available as the
`boomi-tidy-up` skill.

## What to Clean

- `active-development/*/` - All component files
- `active-development/.sync-state/` - Platform sync tracking
- `active-development/feedback/*/` - Test execution results

## How to Execute

Run this cleanup from the project root:

```bash
# Find and remove all files except .gitkeep in active-development
find active-development -type f ! -name ".gitkeep" -delete 2>/dev/null || true
```

Report what was cleaned and confirm directory structure is preserved.
