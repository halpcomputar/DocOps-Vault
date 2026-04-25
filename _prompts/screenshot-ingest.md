---
created: 2026-04-25
version: 1
tags: [meta, prompt, screenshots]
---

# Screenshot Ingest

Use this prompt with a vision-capable AI tool to turn screenshots into structured artifacts.

## Input Assumptions

- Screenshots live in `raw/screenshots/`.
- The root folder can act as an inbox.
- If the client is already known, screenshots may be placed under `raw/screenshots/<client-slug>/`.

## Prompt

Process one or more screenshots as source evidence.

### 1. Read the Image

Extract:

- visible text
- application or portal context
- dates and timestamps
- client or account identifiers
- error messages
- severity signals
- visible configuration state

If text is unclear, mark it as `[unclear]`.

### 2. Classify Destination

| Screenshot shows | Destination |
|---|---|
| Incident signal, alert, breach indicator, outage evidence | existing incident `evidence.md` or new incident via `incident-ingest.md` |
| Evidence for an existing issue | append to that issue |
| Configuration state | relevant standing note under `applications/`, `infrastructure/`, `domains/`, `website/`, `vendors/`, or `locations/` |
| Troubleshooting activity | `activity/YYYY-MM-DD.md` or `daily/YYYY-MM-DD.md` |
| General reference | `raw/clippings/` or a structured note if it has durable value |

### 3. Rename Rule

If the screenshot has a default OS filename, propose a one-time rename:

`YYYY-MM-DD-<slug>.<ext>`

After this first-touch rename, treat the file as immutable.

### 4. Write Artifact

Structured notes should embed the screenshot:

```markdown
![[YYYY-MM-DD-slug.png]]
```

### 5. Manifest

Update `raw/.ingest-manifest.json` with:

- `source_type: screenshots`
- `pipeline: screenshot-ingest`
- `status: ingested`
- created or updated artifacts

## Ask Before Acting

Ask when:

- client attribution is unclear
- multiple clients are plausible
- the image contains credentials, tokens, private keys, financial data, or sensitive personal data
- the target note is ambiguous
- a batch may belong together but the grouping is unclear

