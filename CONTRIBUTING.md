# Contributing

Contributions are welcome.

DocOps Vault is a starter for source-first operational documentation. The most useful contributions are concrete improvements to folder contracts, ingest prompts, templates, OPSEC guidance, and setup ergonomics.

## Privacy Rules

Do not submit:

- real client or customer names
- real domains, IPs, hostnames, tenant IDs, or organization IDs
- screenshots, transcripts, recordings, emails, logs, reports, or tickets containing private data
- credentials, tokens, private keys, recovery codes, or API keys
- private vendor escalation contacts
- internal infrastructure details
- proprietary company procedures unless you have the right to publish them

Use generic placeholders such as `example-client`, `example.com`, `192.0.2.10`, and `person-name`.

## Contribution License

By submitting a pull request or other contribution, you agree that your contribution is licensed under the Apache License 2.0.

If you do not want your contribution treated this way, mark it clearly as "Not a Contribution."

## Good Contributions

- Keep examples sanitized and generic.
- Prefer simple folder contracts over complex automation.
- Update `VAULT.md`, `CONVENTIONS.md`, `INGEST.md`, or `_prompts/` when changing the model.
- Add OPSEC notes when introducing a workflow that could capture sensitive material.
- Keep this repo usable without requiring a specific AI vendor.

## Pull Request Checklist

- I removed private or client-identifying data.
- I did not include secrets, tokens, raw source material, or real screenshots.
- I updated relevant docs if I changed structure or workflow behavior.
- I understand this contribution is licensed under Apache-2.0.

