# Release and Maintenance

**Purpose:** The canonical release checklist and maintenance expectations for pipeline repos.

This document is intentionally practical: it tells you what “good enough” looks like per tier and what to do before you publish.

Tier expectations: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
Repo baseline requirements: [31-repo-requirements.md](./31-repo-requirements.md).

## Pre-release checks

Before publishing a release (or making a repo public), verify:

### Safety and hygiene

- No secrets or credentials are present (including in git history if possible).
- No internal-only references exist (internal URLs, code names, internal docs, internal paths).
- README accurately states tier and support posture.
- Security reporting path exists and is linked (especially Incubating+).

Security guidance: [33-security-and-responsible-disclosure.md](./33-security-and-responsible-disclosure.md).

### Licensing and third-party notices

- License is Apache-2.0 (or approved exception).
- Third-party dependencies are understood; add `THIRD_PARTY_NOTICES` if you bundle third-party code or need explicit attribution.

Legal guidance: [34-legal-and-licensing.md](./34-legal-and-licensing.md).

### Build and documentation

- Project can be built/run from a clean checkout (document steps in README).
- CI passes on default branch.
- “How to try it” is clear enough for a new user to succeed quickly.

## Versioning guidance

Versioning communicates stability to users. Pick the simplest scheme that matches your tier.

### Experimental

Recommended:

- `release.versioning: none` or `date`
- If you publish versions, treat them as “iteration markers,” not stability promises.

### Incubating

Recommended:

- `release.versioning: semver` (common) or `date` (acceptable for some tooling)
- `release.current_version` must be set (schema requirement).
- Publish compatibility expectations (MongoDB versions, runtimes/frameworks where relevant).

### Supported

Required:

- `release.versioning: semver` (schema requirement)
- Use SemVer with clear rules for breaking changes and deprecations.

Schema reference: `playbook/schemas/pipeline.schema.json`.

## Release artifact expectations

Release artifacts should be proportional to the project and its users.

### Minimum expectation (all tiers)

- Provide a tagged release (or documented “how to use main”) appropriate to the repo.
- Include release notes that explain what changed (even if short).

### Common artifact patterns

- `source` (always acceptable)
- `docker` (for services or deployable components)
- `npm`, `pypi`, `maven`, `rubygems` (for libraries)

If you publish packages, ensure:

- package name is stable and documented
- install steps are in README
- compatibility and breaking changes are called out clearly

## Maintenance expectations

Maintenance expectations are tier-dependent. The program values honesty: if you cannot maintain a tier’s promises, demote.

### Experimental

- Best-effort responses; no SLAs.
- Keep tier signaling accurate.
- Periodic heartbeat (review) per [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).

### Incubating

- Responsive triage posture consistent with support statement.
- Keep CI green; do not leave default branch broken.
- Publish periodic releases when meaningful changes ship.
- Maintain compatibility docs and `release.current_version`.

### Supported

- Predictable release cadence and SemVer change management.
- Clear deprecation and breaking-change communication.
- Sponsor PM and exit plan tracked until relocation.

Supported and exit guidance: [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md).

## Deprecation guidance (how to communicate)

Deprecation reduces user risk by discouraging new adoption before archiving.

Recommended steps:

1. Update `pipeline.yaml`:
   - set `retirement.status: deprecated`
   - set `retirement.message` with a clear timeline/intent
   - add `retirement.alternatives` (even if “no direct alternative”)
2. Update `README.md` with a prominent deprecation banner and migration guidance.
3. Publish a showcase update explaining why and what to do next.
4. When archiving, follow the “Retired” requirements (tier + sunset date + archived status).

Tier and retirement details: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
Tier-change process: [12-promotion-and-demotion.md](./12-promotion-and-demotion.md).
Showcase guidance: [41-showcase-program.md](./41-showcase-program.md).
