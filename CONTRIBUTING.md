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
- **Regression tests are mandatory** for bug fixes and new endpoints. If your change fixes a bug, include a test that would have caught it. Config-only changes (env vars, deploy scripts) are exempt.

## Commit Hygiene

- Use clear commit messages.
- Avoid unrelated refactors in task-focused PRs.
