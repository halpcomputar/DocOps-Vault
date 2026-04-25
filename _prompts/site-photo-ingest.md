---
created: 2026-04-25
version: 1
tags: [meta, prompt, site-photos]
---

# Site Photo Ingest

Use this prompt with a vision-capable AI tool to turn site photos into structured infrastructure, project, issue, or incident notes.

## Input Assumptions

Preferred source shape:

`raw/site-photos/<client-slug>/YYYY-MM-DD-<visit-slug>/`

All photos in one session folder should belong to the same client and visit.

## Prompt

Process the site-photo session folder.

### 1. Inspect Every Photo

Extract:

- visible labels
- device names
- model numbers
- serial numbers when appropriate
- port labels
- cabling observations
- rack or room layout
- whiteboard text
- condition issues
- safety or security concerns

Do not invent unreadable labels.

### 2. Classify Output

Use the best destination:

- project note for onboarding, migration, or site visit work
- issue note for a specific problem
- incident evidence for security or outage work
- standing infrastructure note for durable reference facts
- location note for site-specific context

### 3. Write Structured Notes

Embed photos from raw:

```markdown
![[photo-filename.jpg]]
```

Summarize evidence, then extract durable facts into standing notes.

### 4. Manifest

Update `raw/.ingest-manifest.json` for the photo session:

- `source_type: site-photos`
- `pipeline: site-photo-ingest`
- `status: ingested`
- artifacts created or updated

## Ask Before Acting

Ask when:

- the session may contain more than one client or visit
- photos contain sensitive information that should be redacted
- device labels are unreadable but important
- the output could be either an issue or an incident

