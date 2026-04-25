# Industry Profiles Roadmap

DocOps Vault v1 is IT/MSP-first. That is intentional.

The broader pattern can support other work domains, but each domain needs a real folder contract, source model, and output taxonomy. Generic templates are less useful than concrete profiles.

## Core Pattern

Every profile should define:

- raw source types
- structured destination folders
- required standing reference notes
- event/project/incident shapes
- ingest prompts
- privacy constraints
- export targets, if any

## Candidate Profiles

### IT / MSP

Current default.

Focus:

- clients
- applications
- infrastructure
- incidents
- domains
- vendors
- projects
- issues

### OSINT / Investigations

Potential profile.

Possible structure:

- subjects
- organizations
- assets
- sources
- timelines
- leads
- evidence
- reports

Key challenge:

- evidence handling, confidence labels, and legal/ethical constraints matter more than convenience.

### Legal / Case Work

Potential profile.

Possible structure:

- matters
- parties
- evidence
- discovery
- filings
- timelines
- research
- correspondence

Key challenge:

- privilege, jurisdiction, retention, and source traceability need stronger rules than the IT profile.

### Sales / Account Management

Potential profile.

Possible structure:

- accounts
- contacts
- opportunities
- calls
- proposals
- objections
- renewals
- vendors

Key challenge:

- CRMs already exist, so the vault must add value without becoming a worse CRM.

### Research

Potential profile.

Possible structure:

- sources
- notes
- claims
- experiments
- datasets
- synthesis
- open questions

Key challenge:

- citations and claim provenance need to be first-class.

## Initialization Script Idea

A later version could include:

- `init.sh` for macOS/Linux
- `init.ps1` for Windows
- profile selection during setup
- vault root selection
- optional Obsidian config seeding
- optional plugin recommendation output

This should wait until at least one non-IT profile has a real contributor who understands that domain.

## Contribution Rule

New profiles should come from people who actually do that work. AI can help format and normalize the profile, but domain judgment should come from practitioners.

