# KeePass → Bitwarden skills

Practical, security-first guidance for recovering an incomplete migration, preserving newer Bitwarden data, and simplifying a messy vault.

**Four harness-neutral [Agent Skills](https://agentskills.io/specification), not another migration application.** There is no vault reader, secret broker, custom encryption, or unattended writer in this repository. Prefer native product features and small, verified changes.

| Skill | Use it for |
| --- | --- |
| [vault-migration-audit](skills/vault-migration-audit/SKILL.md) | Read-only inventory, conflicts, missing records/files and coverage gaps. |
| [keepass-bitwarden-migration](skills/keepass-bitwarden-migration/SKILL.md) | Approved imports and recovery with encrypted backups and readback. |
| [bitwarden-vault-cleanup](skills/bitwarden-vault-cleanup/SKILL.md) | Verified duplicate removal, simpler folders, native types and icon privacy. |
| [vault-account-separation](skills/vault-account-separation/SKILL.md) | Scoped personal/work copies and decisions about account access. |

## Use with your harness

1. Clone or download this repository and review the relevant skill before installing it. Pin a reviewed commit if your installation mechanism supports that.
2. For an Agent Skills-compatible harness, install the selected directory under `skills/` using **that harness's documented skill mechanism**. Include its `references/` directory. There are no vendor-specific hooks or tool names.
3. If your harness does not discover `SKILL.md`, load the file as instructions/context and make its linked reference available. The documents also work as an attended checklist without an agent.
4. Start with the audit. Load recovery, cleanup or account separation only when that phase is needed and authorized. No Python package is required to read or use these skills.

Example request:

> Use vault-migration-audit to plan a read-only comparison. Keep secret-bearing work in trusted local tools and show only sanitized counts and discrepancy categories. Do not change either vault.

A skill is not a permission grant or a security sandbox. Different harnesses capture tool output, screenshots and approvals differently. **If yours cannot keep decrypted data out of model context and transcripts, use it for planning only and perform secret-bearing work in native applications.** Do not improvise a credential wrapper to get around that limitation.

## The short workflow

**Audit → preserve recoverable backups → approve a concrete change → apply the smallest supported operation → read back → relock.**

- Treat migration as reconciliation when Bitwarden already contains newer values. Reimporting everything is not a merge strategy.
- Prefer a supported native encrypted KDBX import for an approved whole-source import into an empty destination. Do not build an engine for work the native importer can do.
- Check recycle-bin, Archive, Trash, history and attachment coverage explicitly. Names and counts do not prove file bytes survived.
- Preserve notes and custom fields: API tokens can be anywhere. Do not silently reclassify, rewrite or rotate them.
- Keep one complete survivor before soft-deleting a proven duplicate. Never use expiring Trash as the backup.
- Keep personal/work ownership separate unless sharing is explicitly requested. Collections are an access/ownership decision, not another folder style.
- After an uncertain write, inspect the target before retrying. Neither imports nor a sequence of CLI operations should be assumed atomic.

### Where data belongs

| Data | Allowed boundary |
| --- | --- |
| Passwords, tokens, decrypted notes, keys, exports and file bytes | Trusted native applications or an already reviewed local integration; **not the model or captured tool output**. |
| Necessary per-record mappings and detailed discrepancy evidence | Restricted local storage, outside source control and cloud-sync directories. |
| Agent-facing progress | Allowlisted counts and fixed labels such as `verified`, `missing`, `conflict`, `deferred` or `failed`; no raw error messages. |
| Examples, tests, issues and PRs | Invented data only; no real vault material, even encrypted. |

Preserve the encrypted source and its unlock factors until the owner explicitly decides otherwise. Removing work copies from a personal account is a later operation, after newer personal-side changes have been reconciled.

## Scope and limits

These are operational playbooks, not a certified security product. Format validation and secret scanning do not prove an agent will obey instructions or that a migration succeeded. Native product features and plan entitlements change; check current documentation and the installed clients before use. References link to official documentation; synthetic examples are labeled as such.

The repository was developed with AI assistance. Automated review is not human review or an external security audit. No live-vault integration tests are included, and no claim is made that every harness/platform has been tested. The format and instructions are portable; secure execution depends on the actual environment.

See [CONTRIBUTING.md](CONTRIBUTING.md) for reproducible checks and contribution/AI policy, [SECURITY.md](SECURITY.md) for private reporting, and [CHANGELOG.md](CHANGELOG.md) for changes. Licensed under [MIT](LICENSE). Unaffiliated with Bitwarden or the KeePass/KeePassXC projects.
