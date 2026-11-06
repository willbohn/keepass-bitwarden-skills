# Synthetic cleanup decisions

These examples use invented records, not operational receipts.

| Situation | Decision |
| --- | --- |
| Two “Example Mail” records have different note text | Conflict; preserve both until local review. |
| One duplicate has the only file attachment | It is not redundant until a complete survivor is byte-verified. |
| A replacement lacks the original passkey | Keep the original; cloning is not passkey migration. |
| `Work` has no direct items but `Work/Clients` exists | Keep the parent row so nesting remains usable. |
| `Work · Clients` exists but `Work` is unused | The middle dot is leaf text, not a slash-parent relationship. Evaluate actual references. |
| An archived record uses an otherwise empty folder | The folder is referenced; it is not empty for cleanup purposes. |
| Two flattened paths would produce the same name | Reject the naming plan before any rename. |
| Icons are absent in an uninspected client | Unverified UI state; do not change appearance settings or URIs. |

If an external adapter is used, change only approved fields and allow only justified, field-specific, bounded equivalence; keep secret content strict. Do not build a new comparator for a small native cleanup.

A quiet vault and a local lock do not make native operations atomic. Check for intervening edits and stop if the approved before-state no longer holds. Preserve records changed by another client rather than overwriting them during rollback.
