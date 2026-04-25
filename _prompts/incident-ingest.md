---
created: 2026-04-25
version: 1
tags: [meta, prompt, incidents]
---

# Incident Ingest

Use this prompt when raw sources describe a breach, attempted intrusion, outage, forensic investigation, or other security/availability event that deserves a folderized incident record.

This is a destination workflow, not a media-source workflow. It can be invoked directly against `raw/incidents/` case-intake folders or handed off from source-specific pipelines such as transcript, screenshot, report, email, recording, or site-photo ingest.

## Input Assumptions

- Raw sources may come from `raw/incidents/`, `raw/transcripts/`, `raw/emails/`, `raw/reports/`, `raw/screenshots/`, `raw/site-photos/`, or `raw/recordings/`.
- `raw/incidents/<client-slug>/YYYY-MM-DD-<slug>/` is an explicit case-intake path for known incident material.
- The client exists at `it-operations/clients/<client-slug>/`.
- The canonical docs are `VAULT.md`, `CONVENTIONS.md`, and `INGEST.md`.

## Prompt

Build or update an incident record from one or more raw sources.

### 1. Determine Entry Path

There are two valid entry paths:

- **Explicit case intake:** the user points at `raw/incidents/<client-slug>/YYYY-MM-DD-<slug>/`. Treat the folder as known incident material unless the contents clearly contradict that.
- **Source-pipeline handoff:** transcript, screenshot, report, email, recording, or site-photo ingest detects incident relevance and hands off the source to this workflow.

Do not require raw files to be moved into `raw/incidents/` before they can become incident evidence. The source file's physical location describes source type; the manifest records the incident artifact it produced.

### 2. Confirm Incident Scope

Use this workflow for:

- unauthorized access
- attempted intrusion
- ransomware or malware response
- outage root-cause investigation
- forensic evidence collection
- security containment or remediation

If the work is ordinary support or a planned project, route it elsewhere.

### 3. Incident Path

Incident folders live at:

`it-operations/clients/<client-slug>/incidents/YYYY-MM-DD-<slug>/`

Rules:

- use the earliest known incident date
- use a slug based on the incident itself
- update an existing incident folder if one already matches

### 4. Files

Default files:

- `incident.md`
- `timeline.md`
- `evidence.md`

Create `remediation.md` when there is live containment, recovery, or hardening work.

### 5. `incident.md`

Frontmatter:

```yaml
---
created: <today>
updated: <today>
client: <client-slug>
type: incident
status: active | contained | monitoring | closed
severity: low | medium | high | critical
opened: <incident start date>
source:
  - raw/transcripts/example.md
tags: [incident, security]
---
```

Body sections:

- Summary
- Scope
- Current status
- Impact
- Best current root-cause understanding
- Open questions
- Related notes
- Source

### 6. `timeline.md`

Chronological event log with observed sequence, decisions, containment steps, and follow-up actions.

### 7. `evidence.md`

Evidence record with:

- observed facts
- indicators and logs
- environment context
- hypotheses and confidence
- source map

### 8. `remediation.md`

Use when the incident has active follow-up.

Open tasks should use the vault owner's preferred Obsidian task due-date syntax:

```markdown
- [ ] **Owner** - task text due: YYYY-MM-DD
```

### 9. Standing Updates

If the incident changes durable client knowledge, update:

- `infrastructure/`
- `applications/`
- `domains/`
- `vendors/`
- `locations/`

### 10. Manifest

For each raw source processed:

- set `status: ingested`
- set `pipeline:` to `incident-ingest` or the source-specific pipeline
- add incident files to `artifacts`

## Content Rules

- Do not copy secrets or sensitive data wholesale.
- Keep evidence summaries specific.
- Preserve uncertainty.
- Separate confirmed observations from inferred attacker behavior.
