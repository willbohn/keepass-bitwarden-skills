# Working on these skills

This is a documentation-first collection of portable Agent Skills, not a vault client.

- Keep each `skills/*/SKILL.md` independently usable. Put optional detail in its own `references/` directory. Do not require a particular harness, provider, operating system, or local installation.
- Keep credentials and private metadata out of this repository, including encrypted databases, exports, screenshots, operational receipts, and real incident transcripts. Use invented examples and reserved example domains.
- Prefer native product features and existing validation tools. Do not add a migration engine, secret broker, custom cryptography, or a general-purpose framework.
- Vault changes require explicit scope, verified recoverable backups, readback, and deterministic relocking. Skills are guidance, not a sandbox or authorization grant.
- See [CONTRIBUTING.md](CONTRIBUTING.md) for checks, review and AI policy, [SECURITY.md](SECURITY.md) for reporting, and [CHANGELOG.md](CHANGELOG.md) for user-visible changes.
