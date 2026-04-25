# Agent Instructions

This vault uses source-first documentation operations.

Before editing, read:

- `VAULT.md`
- `CONVENTIONS.md`
- `INGEST.md`

## Trust Model

- `raw/` contains source material. Treat it as immutable evidence.
- `it-operations/`, `personal/`, and `daily/` contain human-usable structured notes.
- `_prompts/` contains portable AI workflow specs.
- `wiki/` is optional synthesis and should not be a dependency for core workflows.

## Operating Rules

- Do not invent clients, vendors, attendees, facts, or file routes.
- If source attribution is unclear, ask before routing.
- Do not copy secrets, tokens, private keys, or sensitive personal data into structured notes.
- Do not move raw files after ingest. Screenshots may be renamed once during first-touch ingest if the prompt calls for it.
- Update `raw/.ingest-manifest.json` when processing raw sources.
- Prefer updating existing project, issue, incident, or standing reference notes over creating duplicates.

## Common Workflows

- Client bootstrap: copy `it-operations/clients/_template/` to `it-operations/clients/<client-slug>/`.
- Transcript ingest: follow `_prompts/transcript-ingest.md`.
- Incident ingest: follow `_prompts/incident-ingest.md`.
- Screenshot ingest: follow `_prompts/screenshot-ingest.md`.
- Site photo ingest: follow `_prompts/site-photo-ingest.md`.
- Quicknote ingest: follow `_prompts/quicknote-ingest.md`.
- Diagram ingest: follow `_prompts/diagram-ingest.md`.

## Out of Scope

- Credentials belong in a password manager, not this vault.
- External documentation publishing should be handled by a separate export pipeline.
- This repo is a starter/template. Do not commit private client or source data.
