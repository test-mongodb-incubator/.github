# Tiers and Expectations

**Purpose:** User-facing expectations per tier (the trust contract).

This framework uses tiers to answer one question quickly: **“Should I depend on this, and what can I expect from maintainers?”**

Tiers are communicated in two places:

- `pipeline.yaml` (`project.tier`) for machine-readable discovery.
- `README.md` (tier badge + support statement) for humans.

## Quick guidance (for users)

- If you need long-lived, production-critical dependencies, prefer **Supported**.
- If you’re piloting or adopting early with some risk, **Incubating** can be appropriate.
- If you’re exploring or prototyping, use **Experimental**.
- If a repo is **Retired**, do not adopt it; use the listed alternatives.

## Summary: the trust contract

| Tier | Intended users | Stability guarantees | Support expectations | Release expectations | Required repo hygiene | Deprecation/retirement posture |
|---|---|---|---|---|---|---|
| **Experimental** | Primarily evaluators/early adopters | No API stability guarantees; breaking changes expected | Best-effort; no SLAs | Optional releases; versioning can be `none` or `date` | Minimum viable governance + clear disclaimers | Can be retired quickly with clear message |
| **Incubating** | Wider internal/external usage; early production/pilots | Some stability signals (compatibility stated); breaking changes require notice | Best-effort, responsive maintainers; security reporting path required | Versioned releases expected (`current_version` + compatibility) | Stronger hygiene baseline; periodic review required | Deprecate before archive; provide alternatives when retiring |
| **Supported** | Production workloads and long-lived dependencies | Stronger stability expectations; SemVer required | Product-aligned ownership model; clear support channels | Regular releases and maintenance posture | Highest hygiene baseline; PM sponsor required | “Exit” to long-term home; retirement is a managed process |
| **Retired** | N/A (read-only consumers) | No further changes; archived | No support; issues typically disabled | No releases | Archive state + clear banner | Must include retirement message and alternatives |

If you’re choosing a tier as a builder, start with [01-quickstart-for-builders.md](./01-quickstart-for-builders.md).

## Tier details

### Experimental

**When this tier is appropriate**

- You’re validating a new idea, integration, framework adapter, or tool.
- You want to iterate quickly and gather feedback.
- You cannot yet commit to compatibility, responsiveness, or long-term maintenance.

**User expectations**

- Treat as “safe to evaluate”, not “safe to depend on”.
- Breaking changes can happen at any time without a long deprecation cycle.

**Support expectations**

- Best-effort via GitHub Issues/Discussions.
- No SLAs; response time depends on maintainer availability.
- Recommended support statement pattern: “Experimental: best-effort community support; no SLAs.”

**Release expectations**

- Releases are optional; versioning may be `none` or `date`.
- If you publish releases, document what a version means (even if it’s informal).

**Minimum required metadata (enforced by schema)**

- `audience.intended_users` must be present (e.g., `internal`, `external`, or `both`).
- `release.versioning` must be present.

**Recommended repository hygiene**

- A prominent disclaimer in `README.md` stating the tier and support posture.
- A 5-minute quickstart (or minimal usage example) so evaluators can try it quickly.

### Incubating

**When this tier is appropriate**

- The project has real users (internal or external) and is gaining traction.
- You can commit to basic maintenance and a security reporting path.
- You can publish versioned releases and declare compatibility expectations.

**User expectations**

- Reasonable effort to avoid churn; breaking changes should have notice.
- Compatibility is explicitly stated (MongoDB versions, runtime/framework versions where relevant).

**Support expectations**

- Best-effort, with a bias toward responsiveness and triage.
- A `SECURITY.md` (or equivalent) reporting path is required.
- Recommended support statement pattern: “Incubating: best-effort support; breaking changes possible with notice.”

**Release expectations**

- Versioned releases are expected; `release.current_version` must be set.
- `release.compatibility` must be populated as appropriate for the project.

**Minimum required metadata (enforced by schema)**

- `ownership.maintainers` must be present.
- `support.security_policy_url` must be present.
- `labels.areas` must be present.
- `project.lifecycle.last_reviewed` must be present.
- `release.current_version` and `release.compatibility` must be present.

**Recommended repository hygiene**

- Basic CI appropriate to the repo (lint/test/build).
- Issue triage posture (labels, templates, and a clear “how to get help” section).
- A small “Status / Roadmap” section so users understand direction.

### Supported

**When this tier is appropriate**

- The project is strategically important and should be depended on long-term.
- A product-aligned ownership model exists (a PM sponsor is identified).
- There is a plan to **exit** incubation to a long-term home/org.

**User expectations**

- Stronger stability guarantees and clearer change management.
- Support channels are clear and actively maintained.

**Support expectations**

- Support posture is explicit and reliable relative to incubating tiers.
- Still GitHub-native (issues/discussions), but with committed ownership.
- Recommended support statement pattern: “Supported: maintained with committed ownership; see support channels for details.”

**Release expectations**

- SemVer is required (`release.versioning: semver`).
- `release.current_version` must be set and maintained.

**Minimum required metadata (enforced by schema)**

- `ownership.maintainers` and `ownership.sponsor_pm.github` must be present.
- `project.lifecycle.last_reviewed` must be present.
- `release.versioning` must be `semver`, and `release.current_version` must be present.

**Repository hygiene**

- Highest standard within the pipeline: clear docs, predictable releases, healthy triage.
- Defined process for breaking changes and deprecations.

Exit guidance: [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md).

### Retired

**When this tier is appropriate**

- The project is no longer maintained, is superseded, or no longer fits strategy.
- You want to reduce user risk by making the status unambiguous.

**User expectations**

- The repo is archived or effectively read-only.
- Users should migrate to an alternative.

**Support expectations**

- No support; issues/discussions may be locked or disabled.

**Release expectations**

- No further releases.

**Minimum required metadata (enforced by schema)**

- `project.lifecycle.sunset_date` must be present.
- `retirement.status` must be `archived`.
- `retirement.message` and `retirement.alternatives` must be present.

**Retirement hygiene**

- Add a top-of-README banner stating the project is retired/archived and pointing to alternatives.
- Publish a final showcase update explaining the retirement decision and migration guidance.

## Deprecation before retirement

Deprecation is how we reduce user risk before archiving a repo.

Typical sequence:

1. Set `retirement.status: deprecated` and add a clear `retirement.message`.
2. Add `retirement.alternatives` (even if it’s “no direct alternative; this repo is archived for reference”).
3. Add a prominent deprecation banner to `README.md`.
4. Publish a showcase update explaining timeline and migration guidance.
5. When you’re ready to archive, set `project.tier: retired`, set `project.lifecycle.sunset_date`, and set `retirement.status: archived`.

## Common requirements across tiers

Regardless of tier, every project should have:

- Clear ownership and contact (`pipeline.yaml` + maintainers listed).
- A support statement and support channels.
- A license and contribution path.

Canonical repo requirements: [31-repo-requirements.md](./31-repo-requirements.md).
Promotion/demotion criteria: [12-promotion-and-demotion.md](./12-promotion-and-demotion.md).
Metadata and directory: [40-directory-and-metadata.md](./40-directory-and-metadata.md).
Showcase expectations: [41-showcase-program.md](./41-showcase-program.md).
Release guidance: [32-release-and-maintenance.md](./32-release-and-maintenance.md).
Security and disclosure: [33-security-and-responsible-disclosure.md](./33-security-and-responsible-disclosure.md).
Legal and licensing: [34-legal-and-licensing.md](./34-legal-and-licensing.md).
