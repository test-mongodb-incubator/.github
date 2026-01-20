# Repository Requirements

**Purpose:** Definitive list of required files and conventions for projects in the pipeline.

These requirements exist to ensure:

- Users can quickly understand maturity and support posture.
- The directory can reliably discover and classify repos.
- Projects remain safe to consume and contribute to.

Tier expectations: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
Metadata contract: [40-directory-and-metadata.md](./40-directory-and-metadata.md).

## Required root files

Every pipeline repo must include (in the repo root):

- `README.md`
- `LICENSE`
- `CONTRIBUTING.md`
- `SECURITY.md`
- `pipeline.yaml`

Some repos may also need:

- `THIRD_PARTY_NOTICES` (or `THIRD_PARTY_NOTICES.md`) if third-party OSS is included.

Legal guidance: [34-legal-and-licensing.md](./34-legal-and-licensing.md).

### `README.md` (minimum)

Your README must include, near the top:

- What it is and who it’s for
- Tier + support statement (explicit; do not imply official product support unless true)
- How to try it quickly (example/quickstart)
- Where to get help (issues/discussions links)

Builder quickstart: [01-quickstart-for-builders.md](./01-quickstart-for-builders.md).

### `LICENSE`

- Default license is Apache-2.0 unless an exception is approved.

### `CONTRIBUTING.md`

Must include:

- How to propose changes (issues/discussions)
- How to run tests/build (or where to find instructions)
- CLA expectations (if required)

### `SECURITY.md`

Must include:

- How to report vulnerabilities (private channel preferred over public issues)
- Expected response posture (even if “best-effort”)

Security guidance: [33-security-and-responsible-disclosure.md](./33-security-and-responsible-disclosure.md).

## Required metadata (`pipeline.yaml`)

`pipeline.yaml` is the source of truth for directory metadata and tier signaling. It must validate against:

- `playbook/schemas/pipeline.schema.json`

Tier-specific required metadata is enforced by the schema; do not “hand-wave” it in README only.

## Required tier signaling (badge + support statement)

Every repo must make its tier visible in the README, using:

- A tier badge or prominent tier label
- A one-line support statement consistent with the tier

Recommended support statement patterns:

- Experimental: “Experimental: best-effort community support; no SLAs.”
- Incubating: “Incubating: best-effort support; breaking changes possible with notice.”
- Supported: “Supported: maintained with committed ownership; see support channels for details.”
- Retired: “Retired/Archived: no longer maintained; see alternatives.”

## Required CI baseline

CI should be proportional to tier and language, but must exist.

Minimum expectations:

- **Experimental:** at least one CI workflow that runs on PRs (lint/test/build as appropriate).
- **Incubating:** CI must be reliable on default branch; failing builds should be treated as health issues.
- **Supported:** CI must be reliable; releases should be automated where reasonable.

If a repo cannot be built/tested automatically (rare), the README must explain how validation is performed.

Release guidance: [32-release-and-maintenance.md](./32-release-and-maintenance.md).
Health expectations: [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).

## Naming conventions

Follow org naming guidance (to improve discovery and reduce ambiguity). See:

- `STRUCTURE.md`

## Tagging conventions (topics)

Each repo should set GitHub topics for discovery and filtering. Recommended topics include:

- Tier topic (if you adopt this convention): `tier-experimental`, `tier-incubating`, `tier-supported`, `tier-retired`
- Area/topic tags: `ai`, `framework`, `tooling`, language/framework tags (e.g., `python`, `nodejs`, `spring`, `langchain`)
- `mongodb` (or a consistent org convention) for ecosystem grouping

The directory should also be able to classify repos from `pipeline.yaml` labels:

- `labels.areas`
- `labels.keywords`

## Enforcement (recommended)

To keep the program consistent at scale, enforce requirements via GitHub Actions:

- Validate `pipeline.yaml` against the schema.
- Check required files exist.
- Flag stale `project.lifecycle.last_reviewed` where applicable.

Directory mechanics and validator integration: [40-directory-and-metadata.md](./40-directory-and-metadata.md).
