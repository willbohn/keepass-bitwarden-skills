# Contributing

Keep the collection small, practical and harness-neutral. Fix a concrete gap in a skill before adding another skill, abstraction or tool. Discuss a new executable vault reader/writer separately; it is outside this repository's current scope.

## Content and review

- Use invented examples and reserved domains such as `example.org`. Never submit databases, exports, auth caches, key material, screenshots, operational reports or private identifiers—even encrypted or allegedly redacted ones.
- Each skill must carry its own essential safety boundaries. Optional details belong in that skill's `references/` directory; no dependency on a particular harness or an unrelated local skill.
- Check claims against current official product documentation and distinguish observed behavior from hypotheses. Do not preserve an old workaround as a universal rule.
- Include a relevant synthetic decision example for changed operational guidance. Review its expected outcome; schema validation does not evaluate the safety of the prose.
- Changes affecting secret handling, destructive actions or access/ownership need focused independent review. State whether that review was human or automated. Routine prose fixes do not need a new ceremony.
- Record user-visible changes under `Unreleased` in [CHANGELOG.md](CHANGELOG.md). Use a focused pull request; do not bypass required checks.

## Checks

The skills themselves have no runtime dependencies. The following maintainer commands use Git, Python 3.11+ and [uv](https://docs.astral.sh/uv/) in a POSIX shell. Run from this repository's root. Choose an empty temporary path outside the repository for `VALIDATOR_DIR`.

```sh
VALIDATOR_DIR="$(mktemp -d)"
git clone https://github.com/agentskills/agentskills.git "$VALIDATOR_DIR"
git -C "$VALIDATOR_DIR" checkout --detach 83021e2be457a9b6679148719c1f6074f0ad975e
uv sync --frozen --no-dev --project "$VALIDATOR_DIR/skills-ref"
for skill in skills/*; do
  uv run --frozen --no-dev --project "$VALIDATOR_DIR/skills-ref" skills-ref validate "$PWD/$skill"
done
git diff --check
gitleaks dir --redact --no-banner .
gitleaks git --redact --no-banner --log-opts="--all" .
```

The pinned upstream reference validator and its lockfile check Agent Skills package syntax; they are not migration software. CI runs that validator and pinned Gitleaks with read-only permissions. Review relative links and the actual staged files before publishing; scanners cannot detect every disclosure or unsafe instruction. Never put secret data in the checkout and rely on `.gitignore` to protect it.

There is no custom test framework or production-code test suite. The synthetic tables in each skill's reference document are review cases, not claims of live API or agent-behavior tests.

## AI assistance and conduct

AI-assisted code, documentation, tests, issues and reviews are welcome. Disclose material assistance in the PR, verify the result, and describe limitations accurately. Do not claim another person reviewed or authored unaided work without evidence. Maintainers may use automated reviews; CI does not prove human understanding.

Be respectful, specific and constructive. Do not post sensitive user data, harassment or unsupported security allegations. Report vulnerabilities through the private process in [SECURITY.md](SECURITY.md).
