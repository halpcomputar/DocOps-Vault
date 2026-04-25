---
created: 2026-04-25
tags: [meta, conventions, vault]
---

# Vault Conventions

These rules apply across the structured vault layer.

## Naming

- Filenames use `kebab-case`.
- Client folders use readable slugs, such as `example-client`.
- Use date prefixes only where chronological browsing matters.

## Date-Prefixed Items

Use `YYYY-MM-DD-<slug>` for:

- project folders
- incidents
- issues
- activity notes
- event notes
- dated internal work notes

## Standing Reference Items

Do not use date prefixes for:

- `context.md`
- application notes
- infrastructure notes
- domain notes
- location notes
- vendor notes
- website notes
- SOP notes
- internal people notes
- internal vendor/org notes

## Frontmatter Minimum

```yaml
---
created: YYYY-MM-DD
tags: []
---
```

Add fields only when they improve routing or querying.

Common useful fields:

- `updated:`
- `client:`
- `type:`
- `status:`
- `source:`
- `transcript:`
- `related:`

## Client Context

Each client has a `context.md` quick-reference note.

It should hold:

- business identity
- ownership or parent relationships
- important contacts
- management scope
- tenant or identity headline
- standing quirks and gotchas
- external documentation system mapping, if used

Suggested mapping shape:

```yaml
documentation:
  system: hudu | it-glue | confluence | other
  organization_id:
  organization_name:
```

## Project Folders

Projects live at:

`it-operations/clients/<client-slug>/projects/YYYY-MM-DD-<slug>/`

Each project folder must have:

- `project.md`

## Incident Folders

Incidents live at:

`it-operations/clients/<client-slug>/incidents/YYYY-MM-DD-<slug>/`

Default files:

- `incident.md`
- `timeline.md`
- `evidence.md`

Add `remediation.md` when the incident still has containment, recovery, or hardening work.

## Application Notes

Applications start as flat notes:

`it-operations/clients/<client-slug>/applications/<app>.md`

If an application grows too large, promote it into a folder later.

## Infrastructure Notes

Start with a few canonical notes:

- `internet-wan.md`
- `lan-dhcp.md`
- `wireless.md`
- `vpn.md`
- `compute.md`
- `printers.md`
- `security-cameras.md`

Expand only when a note becomes too crowded.

## Internal People and Vendor Context

Use:

- `it-operations/internal/people/<person-slug>/_person.md`
- `it-operations/internal/vendors/<vendor-slug>/_org.md`

These notes hold durable relationship context, ongoing threads, and links to relevant work artifacts.

## Tags

Keep tags narrow and low-noise.

Recommended pattern:

1. primary type tag
2. scope tag
3. client slug tag if useful
4. topical tags only when useful

Common primary type tags:

- `issue`
- `incident`
- `project`
- `application`
- `infrastructure`
- `domain`
- `vendor`
- `activity`
- `meeting`
- `daily`

## Backlinks

Minimum expectations:

- source-driven notes link back to raw source material
- project notes link related issues, incidents, applications, and infrastructure notes
- incident notes link raw evidence and remediation notes
- standing notes link the projects, issues, or incidents that changed them

## Avoid

- generic dump folders in the structured layer
- category names that describe workflow state instead of content
- duplicate standing facts across many notes
- committing private raw data to a shareable repo

## Related

- [[VAULT]]
- [[INGEST]]

