# Legasi — Engineering & Contribution Standards (Org-wide)

This repository (`legasicrypto/.github`) defines **organization-wide defaults** for Legasi:
- contribution standards (humans + AI agents)
- security policy and reporting
- PR/issue templates
- CODEOWNERS defaults and review expectations (where applicable)

> Public note: This repo is intentionally **safe-to-share**. It does **not** contain secrets, internal IPs/ports, cloud topology details, or operational runbooks.

---

## What is Legasi?

Legasi is building **credit infrastructure** with a strong emphasis on:
- **auditability** and **determinism** (verifiable behavior, reproducible builds)
- **secure service boundaries** (explicit contracts between services)
- **operational readiness** (staging → production promotion with evidence)

The project is early-stage; the focus is on building a foundation where **bad changes are hard to merge** and **claims are never accepted without proof** (CI evidence > prose).

---

## Repositories

### Core repositories

- **`credit-infrastructure`** (monorepo)  
  The canonical codebase for the platform:
  - apps (API/orchestrator, contract-api, indexer, risk-engine scaffolding, etc.)
  - packages (OpenAPI contracts, shared bindings, pure core libs)
  - CI gates (merge-gate / ci-preflight, security scans, etc.)

- **`credit-infrastructure-custody`** (separate by design)  
  Custody “bridge” service (e.g., Fireblocks integration) with strict boundary:
  - communicates with the platform via **HTTP + OpenAPI contract** (no shared code imports)

- **`credit-infrastructure-onchain`**  
  On-chain components (Soroban/Stellar smart contracts, and related tooling).  
  This repo remains separate and is treated as its own security domain.

### Legacy / deprecated repositories

- **`credit-infrastructure-api`**, **`credit-infrastructure-index`**  
  Deprecated in favor of monorepo apps. Kept for reference/rollback during migration windows.

---

## Access model: Private vs Internal

GitHub visibility matters:

- **Private**: only explicit collaborators/teams can access.
- **Internal**: accessible to **organization members** (and sometimes enterprise members), but still **not public**.

If someone gets a **404** on an internal repo, it usually means:
1) they are **not a member of the `legasicrypto` org** (or not in the enterprise), or  
2) they have not completed **SSO authorization** (if enforced), or  
3) they are using the wrong GitHub account.

**Rule of thumb:** switching a repo to *internal* does not grant access to “external people” — it grants access to **org members**.

---

## Contribution philosophy (humans + AI)

### Evidence-only engineering

We operate with a strict rule:

> **No hallucination accepted.**  
> Any claim in a PR must be backed by **CI output**, **tests**, or **code references**.

Examples:
- ✅ “`merge-gate` passed on this PR run” (with CI link)
- ❌ “I tested everything locally and it works” (without evidence)

### PR requirements (baseline)

- PR must include: **What / Why / How to test**
- PR must include **reproducible commands** (or CI links)
- No direct pushes to protected branches
- Required checks must pass (project-specific; enforced in the target repo)

### AI agents

AI agents are welcome contributors, but they are treated as **untrusted**:
- they must work on feature branches
- they must produce verifiable proof (CI logs, tests, lint/typecheck)
- they must not introduce or handle secrets unless explicitly authorized

---

## Environments (high-level)

We use the same principles across environments:

- **Local dev:** Docker compose / mocked deps / deterministic tests
- **Staging:** deployed services with sandbox integrations
- **Production:** deployed services with production integrations + stricter approvals

Operational specifics (IPs, ports, VMs, networks) belong in **private runbooks** inside the implementation repos, not here.

---

## Where are the real docs?

This repo contains org-wide defaults only. For implementation details, see:
- `legasicrypto/credit-infrastructure` → `README.md`, `AGENTS.md`, `docs/`
- `legasicrypto/credit-infrastructure-custody` → service docs + test policy
- `legasicrypto/credit-infrastructure-onchain` → on-chain docs + deployment notes

---

## Security reporting

If you believe you’ve found a security issue:
- follow the instructions in `SECURITY.md` (in this repo)
- do **not** open a public issue with sensitive details

---

## Contact / Ownership

If you need access to an internal repo, or you see a 404:
- confirm org membership
- confirm the GitHub account used
- confirm SSO authorization (if enabled)
- then request access from org admins
