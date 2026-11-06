# Recovery edge cases

## Files and legacy data

An XML export can describe an attachment without providing usable bytes. Do not equate that with an empty attachment. Use the native database to recover the current file, verifying entry identity first; a path/title lookup may select the wrong same-named entry. Test the chosen binary transport with synthetic binary data before using it for real keys or images. A text-oriented stdout path is not a proven binary channel.

Keep current and historical file coverage distinct. An encrypted KDBX retained as a legacy archive preserves source data, but it is not a conversion into native Bitwarden history or icons. It still needs compatible software and the original unlock factors. Attaching a full legacy database to any vault is a separate disclosure/retention decision; never put a mixed personal/work database in a scoped work account.

## Types and fields

Check the actual supported client/server operation before changing an item's type. Do not infer type from a word such as “bank”, “key” or “passport” in its title. A bank website login is still a Login; a PGP key is not an SSH key.

If an in-place conversion is unsupported, a new typed item is a separate replacement operation: obtain approval for a new identity, preserve all old fields and file bytes, verify the replacement, then archive the original if authorized. Retain original history and links. Bitwarden cloning does not copy passkeys; preserve passkey-bearing originals unless an explicitly supported, separately verified transfer is used. Never strip a private-key passphrase or change key formats merely to fit a destination field.

## Failure and verification

| Synthetic situation | Required response |
| --- | --- |
| Backup cannot be decrypted | No write; relock and report the failure. |
| Target changes after approval | Stop and rebuild the comparison; do not adopt the new state as if approved. |
| Create times out | Inspect the exact target and current inventory before deciding whether to retry. |
| File name matches, downloaded bytes differ | Stop; retain both originals and diagnose locally. |
| Readback differs only in one metadata field | Investigate the actual producer and cause. Allow only a justified, bounded equivalence for that field; keep secret content strict. |
| User cancels a secure prompt | Stop the attempted operation, verify lock state and wait; do not keep reopening prompts. |

For large copies, choose a supported bulk operation only when its scope and verification fit. Never switch strategies mid-run or weaken readback for speed. Routine progress needs sparse milestones, not a new approval for each item.
