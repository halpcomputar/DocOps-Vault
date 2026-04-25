---
created: 2026-04-25
version: 1
tags: [meta, prompt, incidents]
---

# Incident Ingest

Use this prompt when raw sources describe a breach, attempted intrusion, outage, forensic investigation, or other security/availability event that deserves a folderized incident record.

## Input Assumptions

- Raw sources may come from `raw/transcripts/`, `raw/emails/`, `raw/reports/`, `raw/screenshots/`, `raw/site-photos/`, or `raw/recordings/`.
- The client exists at `it-operations/clients/<client-slug>/`.
- The canonical docs are `VAULT.md`, `CONVENTIONS.md`, and `INGEST.md`.

## Prompt

Build or update an incident record from one or more raw sources.

### 1. Confirm Incident Scope

Use this workflow for:

- unauthorized access
- attempted intrusion
- ransomware or malware response
- outage root-cause investigation
- forensic evidence collection
- security containment or remediation

If the work is ordinary support or a planned project, route it elsewhere.

### 2. Incident Path

Incident folders live at:

`it-operations/clients/<client-slug>/incidents/YYYY-MM-DD-<slug>/`

Rules:

- use the earliest known incident date
- use a slug based on the incident itself
- update an existing incident folder if one already matches

### 3. Files

Default files:

- `incident.md`
- `timeline.md`
- `evidence.md`

Create `remediation.md` when there is live containment, recovery, or hardening work.

### 4. `incident.md`

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

### 5. `timeline.md`

Chronological event log with observed sequence, decisions, containment steps, and follow-up actions.

### 6. `evidence.md`

Evidence record with:

- observed facts
- indicators and logs
- environment context
- hypotheses and confidence
- source map

### 7. `remediation.md`

Use when the incident has active follow-up.

Open tasks should use the vault owner's preferred Obsidian task due-date syntax:

```markdown
- [ ] **Owner** - task text due: YYYY-MM-DD
```

### 8. Standing Updates

If the incident changes durable client knowledge, update:

- `infrastructure/`
- `applications/`
- `domains/`
- `vendors/`
- `locations/`

### 9. Manifest

For each raw source processed:

- set `status: ingested`
- set `pipeline:` to `incident-ingest` or the source-specific pipeline
- add incident files to `artifacts`

## Content Rules

- Do not copy secrets or sensitive data wholesale.
- Keep evidence summaries specific.
- Preserve uncertainty.
- Separate confirmed observations from inferred attacker behavior.
