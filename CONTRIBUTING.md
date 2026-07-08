# Contributing

## Workflow

1. Create a feature branch from `main`.
2. Keep changes scoped to one task/PR.
3. Run repository tests and checks locally before opening a PR.
4. Open a PR using the template and request review.

## Pull Requests

- Keep PRs small and reviewable.
- Describe what changed, why, and how to test.
- Do not commit secrets, credentials, or generated private keys.
- **Regression tests are mandatory** for bug fixes and new endpoints. If your change fixes a bug, include a test that would have caught it. Exempt only when there is no runtime, deployment, security, or user-visible behavioral effect (e.g. docs, pure visual/copy edits). Anything that changes behavior needs a test.

## Evidence

Every claim — in a PR, a doc, or an external submission — must cite a verifiable artifact:

- a CI run link or pasted command output (for "it works" / "tests pass")
- a code reference (for "the code does X")
- a deployed contract ID, transaction hash, or equivalent on-chain/runtime proof (for "it is live" / "it moved value")

"Tested locally" without pasted output does not count. Claims are written **from** evidence, never written first and verified later. If you cannot produce the artifact, do not make the claim — state what is actually proven instead.

## Commit Hygiene

- Use clear commit messages.
- Avoid unrelated refactors in task-focused PRs.
