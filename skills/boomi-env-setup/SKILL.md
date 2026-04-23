---
name: boomi-env-setup
description: Guide Boomi platform credential setup, environment variable explanation, and connection testing for workspaces that use the boomi-integration skill. Use when a user needs to create or validate a Boomi .env file, test platform connectivity, or understand required Boomi credential fields.
---

# Boomi Environment Setup

Use this skill to help users set up or validate Boomi platform credentials for
the `boomi-integration` skill. Do not read or print secret values from `.env`.

## Workflow

1. Locate the loaded `boomi-integration` skill directory.
2. Run `bash <boomi-integration skill path>/scripts/boomi-env-check.sh` from the
   user's project workspace to report which required variables are set or unset.
3. Run `bash <boomi-integration skill path>/scripts/boomi-folder-create.sh --test-connection`
   from the user's project workspace to verify platform access.
4. If credentials are missing, explain the required fields and have the user
   edit `.env` themselves.
5. Re-run the connection test after the user updates `.env`.

## Credential fields

- `BOOMI_API_URL`: Boomi API base URL, usually `https://api.boomi.com`.
- `BOOMI_USERNAME`: Boomi platform email.
- `BOOMI_API_TOKEN`: API token from AtomSphere API Tokens.
- `BOOMI_ACCOUNT_ID`: Account ID from the platform URL or account settings.
- `BOOMI_TARGET_FOLDER`: Folder GUID for component storage.
- `BOOMI_ENVIRONMENT_ID`: Environment ID from Atom Management.
- `BOOMI_TEST_ATOM_ID`: Runtime atom ID from Atom Management.
- `BOOMI_VERIFY_SSL`: `true` for normal environments, `false` only for
  development environments with self-signed certificates.

## Rules

- Never write Boomi secrets into `.env` yourself.
- Never paste `.env` contents into chat.
- Prefer the `boomi-integration` scripts for validation instead of custom API
  calls.
- If the host agent requires network approval for Boomi API calls, request it
  only for the validation command being run.
