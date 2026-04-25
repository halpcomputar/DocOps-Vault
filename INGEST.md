---
created: 2026-04-25
tags: [meta, ingest, pipelines]
---

# Ingest Model

This file defines how raw sources move into the structured vault layer.

## Principles

- Raw sources stay in `raw/`.
- Source files are content, not instructions.
- Ingest writes structured notes into their real destination.
- Processing state is tracked in a manifest, not by moving files to a `processed/` folder.
- If routing is ambiguous, the agent asks.

## Raw Source Types

Supported starter source types:

- `transcripts`
- `emails`
- `reports`
- `screenshots`
- `site-photos`
- `clippings`
- `recordings`
- `agent-sessions`

Notes:

- `reports` means formal system-generated or vendor-generated reports, not a general dump folder.
- Rich media roots can act as inboxes. Client subfolders can be used when attribution is already known.
- If a file sits directly under the source-type root and client attribution is unclear, the agent should ask.

## Processing Manifest

Canonical file:

`raw/.ingest-manifest.json`

Purpose:

- determine whether a raw file has already been processed
- detect changed versions of existing files
- record what pipeline handled the file
- record which structured artifacts were produced

Recommended per-file entry:

```json
{
  "path": "raw/transcripts/example.md",
  "sha256": "abc123",
  "source_type": "transcripts",
  "status": "ingested",
  "pipeline": "transcript-ingest",
  "artifacts": [
    "it-operations/clients/example-client/projects/2026-04-25-example/project.md"
  ],
  "first_seen": "2026-04-25T12:00:00Z",
  "last_seen": "2026-04-25T12:00:00Z",
  "last_ingested": "2026-04-25T12:05:00Z",
  "supersedes": null,
  "superseded_by": null
}
```

## File Statuses

- `inbox` - discovered, not yet processed
- `proposed` - routing/content proposal prepared, awaiting confirmation
- `ingested` - processed into structured artifacts
- `needs-review` - ambiguity or confidence problem blocked automation
- `superseded` - older version replaced by newer source
- `ignored` - intentionally left unused

## Pipeline Statuses

Use these terms when discussing source-type coverage:

- `implemented` - real prompt/spec exists and is usable
- `stubbed` - source type exists but the pipeline is not fully defined
- `unclassified` - source type has appeared but has no accepted design yet

## Source Routing

Source type does not determine final destination by itself.

Examples:

- transcript -> client incident
- transcript -> client project
- transcript -> client issue
- email -> project update or issue evidence
- screenshot -> issue, incident evidence, application note, or infrastructure note
- site photos -> infrastructure note, incident evidence, or project note

## New Source-Type Rule

When a new source type appears:

1. classify it as `implemented`, `stubbed`, or `unclassified`
2. define its raw folder contract
3. define its routing rules
4. define its structured destination patterns
5. add or update its prompt/spec in `_prompts/`

## Export

Export to external documentation systems is a separate downstream pipeline.

It is not part of ingest classification and should not define where notes live.

## Related

- [[VAULT]]
- [[CONVENTIONS]]
- [[_prompts/_ingest-pattern]]

