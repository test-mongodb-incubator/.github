# Security and Responsible Disclosure

**Purpose:** Make “safe usage” legible for users and contributors, and make security reporting predictable for maintainers.

This program favors clarity over formality. Even Experimental repos must be honest about their security posture.

Repo baseline requirements: [31-repo-requirements.md](./31-repo-requirements.md).
Tier expectations: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).

## Reporting security issues

### Do not report vulnerabilities via public issues

Unless a repo explicitly says otherwise, security vulnerabilities should not be reported in public GitHub issues.

### Where to report

Each repo must provide a `SECURITY.md` that states the preferred reporting mechanism.

In `pipeline.yaml`, `support.security_policy_url` should link to the repo’s `SECURITY.md` (required for Incubating+).

If you are setting up the organization defaults, provide an org-level `SECURITY.md` in `.github` that individual repos can inherit.

## Dependency and update policy (recommended baseline)

Dependencies are one of the largest sources of risk. At minimum:

- Prefer pinned dependency ranges that avoid surprise breaking updates.
- Keep dependencies reasonably up to date, especially security patches.
- Avoid introducing unnecessary dependencies (especially those that execute code at install time).

If your project publishes an artifact (package/image), document:

- supported runtime/framework versions
- supported MongoDB server versions (where relevant)

Release guidance: [32-release-and-maintenance.md](./32-release-and-maintenance.md).

## Secret scanning and provenance expectations

### Secrets

- Never commit credentials, tokens, connection strings with passwords, or private keys.
- Treat sample `.env` files as risky: provide `.env.example` without secrets.
- Rotate credentials immediately if a leak is suspected.

### Supply chain/provenance (recommended)

Depending on tier and artifact type:

- Ensure CI runs on PRs and default branch.
- Use protected branches for Incubating+.
- Prefer reproducible builds where practical.
- For published artifacts, document the build/release process so users can trust provenance.

## Tier-specific security posture

Security posture should be consistent with tier signaling and the support statement.

### Experimental

Minimum:

- `SECURITY.md` exists (even if it says “best-effort”).
- README includes an “Experimental” disclaimer so users do not assume production-grade security review.

Recommended “Experimental caveat” language:

> This project is Experimental. It is provided as-is for evaluation. Use caution in production and review the code and dependencies before deploying.

### Incubating

Minimum:

- `support.security_policy_url` present in `pipeline.yaml` (schema requirement).
- Basic hygiene: dependency updates, CI health, and prompt triage of security reports.

Recommended:

- Consider enabling Dependabot (or equivalent) for dependency updates.
- Document any sensitive handling (credentials, PII, network access) and safe defaults.

### Supported

Minimum:

- Clear ownership and committed maintainers.
- Predictable release process and SemVer change management.

Recommended:

- More formal vulnerability response expectations (even if still “best-effort”).
- Security considerations documented (threat model, safe configuration, hardening guidance) if the project is used in production contexts.

Supported guidance: [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md).

## If a security issue affects tiering

Security posture can drive tier changes:

- If Incubating+ cannot sustain a security reporting path or timely handling, demotion may be recommended to reduce implied promises.
- If a repo is unmaintained and security issues cannot be addressed, retirement may be recommended.

Tier change process: [12-promotion-and-demotion.md](./12-promotion-and-demotion.md).
Review and health escalation: [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).
