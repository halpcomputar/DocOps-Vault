# OPSEC Review Checklist

Use this checklist before making the repo public or publishing a release.

## Do Not Commit

- real client names
- internal client codes
- domains, IPs, hostnames, tenant IDs, or org IDs
- screenshots with visible customer data
- transcripts, emails, recordings, reports, or agent session logs
- documentation platform URLs or IDs tied to real clients
- credentials, tokens, API keys, seed phrases, private keys, or recovery codes
- internal infrastructure details
- private vendor escalation contacts

## Check These Paths

- `raw/`
- `it-operations/clients/`
- `daily/`
- `personal/`
- `.obsidian/`
- `.trash/`
- `.gitignore`

## Recommended Command Sweep

Before publishing, run searches for known private terms:

```sh
rg -n "client-name|internal-domain|private-domain|tenant-id|api-key|password|secret|token" .
```

Also scan for accidental source files:

```sh
find raw it-operations/clients daily personal -type f | sort
```

The template should only contain folder contracts, placeholder notes, and generic docs.

## Documentation System References

Keep provider-specific export details out of the starter unless they are generic enough to apply broadly. Use neutral language such as "external documentation system" unless a guide is explicitly about one product.

