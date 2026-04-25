# DocOps Vault

DocOps Vault is a source-first Obsidian starter for turning raw operational inputs into structured, useful notes with the help of whatever AI tool you prefer.

It is intentionally IT/MSP-flavored in v1. The default work model assumes clients, vendors, applications, infrastructure, incidents, projects, and downstream documentation systems. The core pattern is broader than IT, but the starter templates are optimized for technical operations work.

## Core idea

1. Drop raw source material into `raw/`.
2. Keep those sources immutable.
3. Use AI prompts in `_prompts/` to classify, route, and distill the source.
4. Write structured notes into their real destination under `it-operations/`, `personal/`, or `daily/`.
5. Track processing state in `raw/.ingest-manifest.json`.

This is not "Obsidian RAG" as a vague bucket. It is documentation operations: raw evidence in, durable operational knowledge out.

## Important files

- `VAULT.md` - architecture and intent
- `CONVENTIONS.md` - naming, metadata, links, and folder contracts
- `INGEST.md` - source types, routing, and manifest semantics
- `AGENTS.md` - bootstrap instructions for AI coding agents
- `_prompts/` - portable prompt contracts for source ingest
- `it-operations/clients/_template/` - starter client structure

## Privacy model

This repository contains no example client data and no source material. The `.gitignore` is configured so private raw files, daily notes, personal notes, and client folders created after install are not accidentally committed.

If you make this repo public later, review `docs/OPSEC.md` first.

## Recommended use

Clone or download the repo, open it as an Obsidian vault, then customize:

- rename `it-operations/` if your work domain is not IT
- adjust `it-operations/clients/_template/` for your client model
- update `AGENTS.md` with your preferred AI tooling notes
- add your own source-specific prompts as your ingest needs grow

## Roadmap

The broader idea is to support multiple industry profiles later: IT/MSP, OSINT, legal, sales, research, healthcare-adjacent admin, and other structured knowledge domains. For now, this repo keeps the first profile concrete because concrete systems are easier to improve than generic frameworks.

See `docs/INDUSTRY-PROFILES.md`.

