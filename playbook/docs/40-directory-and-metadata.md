# Directory and Metadata

**Purpose:** Explain how discovery works, and how `pipeline.yaml` keeps the program trustworthy at scale.

The directory is only as good as the metadata. `pipeline.yaml` is the machine-readable contract that powers:

- A browsable directory (“what exists, who owns it, what tier is it?”)
- Tier signaling and user trust (clear support posture)
- Health automation (stale review detection and “still active” heartbeat)

Repo baseline requirements: [31-repo-requirements.md](./31-repo-requirements.md).
Tier expectations: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
Health and heartbeat: [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).

## Why `pipeline.yaml` exists

GitHub repos are easy to create; consistent discovery is not.

`pipeline.yaml` exists so that:

- Humans can quickly find the right project for a use case.
- Users can assess risk (tier + support posture) without guessing.
- The steering committee can reason about the portfolio (ownership, health, adoption signals).
- Automation can validate consistency and prevent drift (schema validation, stale review flags).

## Where `pipeline.yaml` lives

Unless otherwise specified by your templates:

- Put `pipeline.yaml` in the **repo root**.

If you later standardize on a subpath (e.g., `.mongodb/pipeline.yaml`), keep it consistent across all repos and update tooling accordingly.

## Schema and validation

The authoritative schema is:

- `playbook/schemas/pipeline.schema.json`

Validation should run in CI for every repo in the program. Treat schema failures as actionable errors, not as “nice to have” warnings.

## Required vs optional fields

The schema defines:

- **Always-required fields** (must exist for every repo)
- **Tier-gated required fields** (must exist when `project.tier` is a specific value)
- **Optional fields** (high value, but not required)

### Always-required fields (high level)

Every `pipeline.yaml` must include:

- `schema_version`
- `project` (name/description/tier/lifecycle)
- `ownership` (at least an owner)
- `links` (repo URL)
- `support` (statement + at least one channel)
- `compliance` (license + CLA requirement)
- `retirement` (status)

### Optional but high leverage fields

Depending on the project, these are often worth filling in:

- `labels.keywords` (search and discovery)
- `links.docs` and `links.homepage`
- `signals` (internal adoption and community interest)
- `compliance.telemetry` notes (if applicable)

## Tier-specific required metadata (what changes by tier)

Tier-specific requirements are enforced by the schema. This section summarizes the intent (the schema is the source of truth).

### Experimental

Intent: make it safe to evaluate by being explicit about audience and release posture.

Schema-gated requirements include:

- `audience.intended_users`
- `release.versioning`

### Incubating

Intent: stronger hygiene, security reporting, and release/compatibility clarity.

Schema-gated requirements include:

- `ownership.maintainers`
- `support.security_policy_url`
- `labels.areas`
- `project.lifecycle.last_reviewed`
- `release.current_version` and `release.compatibility`

### Supported

Intent: committed ownership and SemVer + an exit plan tracked outside the schema.

Schema-gated requirements include:

- `ownership.maintainers`
- `ownership.sponsor_pm.github`
- `project.lifecycle.last_reviewed`
- `release.versioning: semver`
- `release.current_version`

Supported and exit: [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md).

### Retired

Intent: eliminate user ambiguity and provide alternatives.

Schema-gated requirements include:

- `project.lifecycle.sunset_date`
- `retirement.status: archived`
- `retirement.message` and `retirement.alternatives`

Retirement sequencing: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).

## How the directory gets generated

The directory can be implemented in multiple ways, but the core idea is consistent:

1. **Discover** repos in the org (by topic, allowlist, or GitHub search).
2. **Fetch** each repo’s `pipeline.yaml`.
3. **Validate** it against `playbook/schemas/pipeline.schema.json`.
4. **Aggregate** into a registry (JSON/YAML snapshots).
5. **Render** a human-friendly index (README table, GitHub Pages site, etc.).

Recommended behaviors:

- If metadata is invalid, fail validation and open/flag an issue in the repo (do not silently drop it).
- If `project.lifecycle.last_reviewed` is stale, flag it for health review.

## How to update metadata safely

Metadata changes are user-visible and can affect trust. Treat them like a small release:

### Safe update checklist

- Update `pipeline.yaml` in a PR.
- Ensure schema validation passes in CI.
- If changing tier:
  - update `README.md` tier badge/support statement
  - follow the tier-change process
  - publish a short showcase update explaining why

Tier changes: [12-promotion-and-demotion.md](./12-promotion-and-demotion.md).
Showcase expectations: [41-showcase-program.md](./41-showcase-program.md).

### What should trigger a metadata update

- Owner/maintainers changed
- Support channels changed
- Tier changed
- New release published (update `release.current_version`)
- Compatibility changed
- Quarterly review/heartbeat update (`project.lifecycle.last_reviewed`)
- Deprecation/retirement status changes

## Sample `pipeline.yaml`

This sample is representative of an Incubating project; tailor fields to your tier and project.

```yaml
schema_version: "1.0"

project:
  name: "framework-spring-session-mongodb"
  tagline: "MongoDB-backed Spring Session store"
  description: "A Spring Session implementation backed by MongoDB, intended for modern Spring Boot apps."
  tier: "incubating" # experimental | incubating | supported | retired
  lifecycle:
    created: "2026-01-10"
    last_reviewed: "2026-01-15"
    sunset_date: null

ownership:
  owner:
    name: "Alex Bevilacqua"
    github: "alexbevi"
    org: "MongoDB"
  maintainers:
    - name: "Jane Doe"
      github: "janedoe"
      org: "MongoDB"
  sponsor_pm: # required only for supported
    name: null
    github: null

links:
  repo: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb"
  docs: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/blob/main/README.md"
  homepage: null
  showcase:
    - title: "Initial release + roadmap"
      url: "https://github.com/mongodb-pipeline/showcase/blob/main/posts/2026/01/spring-session-mongodb.md"

labels:
  areas: ["framework", "java", "spring"]
  keywords: ["session", "spring-boot", "mongodb"]

audience:
  intended_users: ["internal", "external"] # internal | external | both
  personas: ["app-dev", "platform-eng"]
  maturity_expectation: "Pre-1.0 API; safe for evaluation and pilots."

support:
  statement: "Incubating: best-effort community support; no SLAs."
  channels:
    - type: "github-issues"
      url: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/issues"
    - type: "discussions"
      url: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/discussions"
  security_policy_url: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/blob/main/SECURITY.md"

release:
  versioning: "semver" # semver | date | none
  current_version: "0.3.0"
  release_artifacts: ["source"] # source | docker | npm | maven | pypi | rubygems | other
  compatibility:
    mongodb: ["6.0+", "7.0+", "8.0+"]
    runtimes: ["Java 17+", "Spring Boot 3.2+"]

compliance:
  license: "Apache-2.0"
  cla_required: true
  third_party_notices: true
  telemetry:
    present: false
    notes: "No telemetry planned."

signals:
  internal_adoption:
    customer_zero_team: "Internal Engineering"
    known_consumers: ["IE Platform Team"]
    known_instances: 2
  community:
    stars: null
    forks: null
    contributors_external: null

retirement:
  status: "active" # active | deprecated | archived
  message: null
  alternatives: []
```

## Common mistakes (and how to avoid them)

- **Tier drift:** `README.md` says one thing, `pipeline.yaml` says another. Keep them consistent.
- **Stale ownership:** owner/maintainers left the team, but metadata never changed. Update promptly.
- **Missing security policy link (Incubating+):** add `SECURITY.md` and set `support.security_policy_url`.
- **Unclear docs links:** set `links.docs` to the best “start here” page (often the README).
- **No heartbeat:** keep `project.lifecycle.last_reviewed` current so users can trust “active” status.
