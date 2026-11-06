# Coverage and synthetic audit examples

These are invented examples, not captured vault records.

| Observation | Safe conclusion and next step |
| --- | --- |
| A KeePass login has no Bitwarden candidate | Missing candidate; inspect locally before creating anything. |
| Two records share a title, but their usernames differ | Not proven duplicates. Preserve both. |
| Destination has a changed password and an extra note | Conflict, not permission to replace it with the source. |
| XML names a file but its binary reference is unresolved | File content is unknown, not absent. Inspect the native source entry. |
| Counts match but different IDs are present | Coverage is not proved. Reconcile identities. |
| No token-like text is detected in notes | Notes remain confidential and must be preserved. |
| A standard export contains no Trash items | Expected format limitation, not proof the Trash is empty. |

A useful local coverage table records source identity, candidate destination identity, lifecycle, matching confidence, fields compared, and file verification status. Even that metadata is private. The model-facing summary normally needs only counts and fixed discrepancy categories, not the table itself.

Inspect history separately from current values. Do not recreate every historical version as a live login. Preserve the encrypted original and state which histories or file versions require reopening it.

Any XML processing must reject DTD/entity declarations and bound input size, expansion and decompression. Do not infer file bytes from an unresolved binary reference. Prefer the native application over a new parser.
