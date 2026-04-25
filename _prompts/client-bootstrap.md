---
created: 2026-04-25
tags: [meta, prompt, client-bootstrap]
---

# Client Bootstrap

Use this when adding a new client to the vault structure.

## Inputs

- client slug
- client display name
- known documentation-system mapping, if any
- any confirmed initial facts

## Prompt

Bootstrap a new client folder in this DocOps Vault.

1. Copy `it-operations/clients/_template/` to `it-operations/clients/<client-slug>/`.
2. Use a readable client slug, not a private internal short code.
3. Populate only confirmed fields in `context.md`.
4. Leave unknowns blank.
5. Do not create project, issue, incident, application, or infrastructure notes unless there is source material for them.

## Output

Report:

- created path
- populated context fields
- unknowns that need owner input
- recommended next ingest action, if source material was provided

