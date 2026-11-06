# Synthetic selection examples

Suppose the owner authorizes an inclusive OR of: an actual ancestor group named `Example Company`; title containing the literal `EXCO`, case-insensitively; or a structured email at `example.org` or a genuine subdomain.

| Invented candidate | Decision |
| --- | --- |
| Child of the actual `Example Company` group | Include by ancestry. |
| A freeform note says `Example Company` | Not a selection signal. |
| Title is `EXCO staging login` | Include by the explicitly approved title predicate. |
| Structured email is `person@example.org` | Include by email. |
| Structured email is `person@team.example.org` | Include if subdomains were explicitly allowed. |
| Structured email is `person@example.org.evil.test` | Do not include by email. |
| A field contains `Person <person@example.org>` but the parser supports only bare addresses | Stop for local review of that candidate; do not silently claim complete email coverage. |
| Structured email has an unexplained trailing suffix | Review; never repair it into an approved identifier automatically. |
| One entry matches every rule | Count it once by source identity. |
| A matching entry is in the recycle bin | Include in the approved scope with retired state preserved, not silently active. |

These predicates are an example, not defaults for another organization. Titles can over-select; show the selected set locally before approval. A domain match is evidence for the approved selection rule, not proof of legal ownership or permission to disclose.

An empty-target writer is intentionally not a merge tool. If it stops after creating some records, inspect live state and receipts privately. Do not run it again, delete the partial destination, or change the expected before-state simply to make a precondition pass.
