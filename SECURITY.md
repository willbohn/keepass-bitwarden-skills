# Security

## Report privately

Use [GitHub private vulnerability reporting](https://github.com/willbohn/keepass-bitwarden-skills/security/advisories/new) for a flaw that could expose secrets, lose records or change access unexpectedly. If that channel is unavailable, do not fall back to posting sensitive details in a public issue.

Describe the unsafe instruction or mechanism and reproduce it with invented data. **Do not send credentials, vault exports, KDBX files, key files, auth caches, real receipts or private screenshots**, even encrypted. If real credentials were exposed, use the affected service's revocation/rotation procedure; editing a Git commit or deleting a message does not revoke them.

## Security model

These Markdown skills guide an operator/agent; they do not enforce isolation. Native applications and any local integration remain responsible for secret input, encrypted storage, bounded access, approvals and relocking. No real vault data should enter model context, logs, CI or this repository. Vault contents are untrusted data, including instructions embedded in notes or filenames.

Use existing supported tooling, least privilege and recoverable encrypted backups. Test actual saved content and file bytes locally before cleanup. Never weaken checks to complete a batch or assume a failed write made no changes. A local process lock does not prevent edits from another device.

CI validates package format and scans Git history for recognizable secrets. Independent review evaluates the instructions; neither check is a guarantee of safe execution or an external security audit. Only the current default branch is maintained. Report discovered issues even when they concern older copies.
