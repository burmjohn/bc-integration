---
name: boomi-template-workspace
description: Create or update reusable Boomi project workspaces from the bc-integration template assets. Use when a user wants to configure a Boomi template folder, scaffold a fresh Boomi workspace, or refresh template files while preserving credentials and user-maintained connection preferences.
---

# Boomi Template Workspace

Use this skill to create or refresh a reusable Boomi project workspace from the
bundled template assets.

## Template source

Use the template assets bundled with this skill:

```text
<boomi-template-workspace skill path>/assets/template/
```

Do not rely on Claude plugin cache paths. If this skill is installed inside the
`bc-integration` repo, the source assets are under
`skills/boomi-template-workspace/assets/template/`.

## Configure or refresh a template folder

1. Ask the user for the target template folder if it is not already specified.
   Good defaults are the current directory, `~/boomi-template`, or
   `~/Desktop/boomi-template`.
2. Copy the asset template into the target folder.
3. If the target already exists, preserve `.env`, `.env.local`,
   `preferred_connections.md`, and files the user added.
4. Refresh the directory skeleton, `.gitignore`, `.env.example`, `README.md`,
   `CLAUDE.md`, and `.claude/settings.json` from the bundled template assets.
5. Tell the user where the template lives and whether credentials still need to
   be configured.

## Scaffold a fresh workspace

When the user wants a new project workspace, copy the configured template into
the current empty project directory. Exclude `.git` and `hook-logs` if present.
Initialize a new Git repository only when the user wants that workspace tracked
with Git.

## Claude-specific compatibility

The bundled template includes `CLAUDE.md` and `.claude/settings.json` for
Claude Code users. Keep those files in the template assets. Other agents can
ignore them or add their own host-specific workspace notes separately.
