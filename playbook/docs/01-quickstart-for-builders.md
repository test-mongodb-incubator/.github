# Quickstart for Builders

**Purpose:** The “I built a thing” guide (builder happy path)

This guide gets your project into the incubator with the minimum required structure, clear expectations, and a repeatable path to publish updates.

## Prereqs

Before you start, make sure you have:

- A GitHub account that can create repos in the incubator org (or a sponsor who can).
- A project that is safe to build **in public** (no internal-only code, no secrets, no confidential docs, no customer data).
- A basic owner/maintainer plan: at least one person who will respond to issues and ship small updates.

Where to ask questions:

- Use the org’s standard support channel for the incubator program (typically GitHub Discussions in the `playbook` repo, or the `intake` repo).
- If you’re unsure whether you can publish something, start an intake issue before creating the repo.

## Choose a tier (Experimental vs Incubating)

Pick the tier that matches your intent **today**. You can change it later.
Whichever tier you choose, keep it consistent across:

- `pipeline.yaml` (`project.tier`)
- Your `README.md` (tier badge + support statement)

### Experimental (default)

Choose **Experimental** if:

- You want to iterate quickly and validate whether the project is useful.
- You can’t commit to strong stability guarantees yet.
- You want visibility and a “safe to evaluate” signal without promising long-term support.

### Incubating

Choose **Incubating** if:

- You already have early adopters (internal or external) and expect others to depend on it.
- You can commit to regular maintenance and basic security hygiene.
- You can publish versioned releases and state compatibility expectations.

If you’re uncertain, start as **Experimental** and promote once you have usage signals.

For detailed tier expectations, see [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).

## Create a repo (recommended: from a template)

1. Choose a repo name that matches the org conventions (see `STRUCTURE.md`).
2. Create the repo from the appropriate org template (if available):
   - `template-experimental`
   - `template-incubating`
3. Set visibility according to program policy (most incubator repos are public).
4. Add standard topics/labels used by the directory (for discovery and automation).

If no templates exist yet, create an empty repo and add the required files in the next section.

## Fill the required files (minimum viable contract)

At minimum, every incubator repo should include:

- `README.md` (what it is, who it’s for, how to try it, current status/tier)
- `LICENSE` (typically Apache-2.0)
- `pipeline.yaml` (metadata used by the directory and automation)

Other required files (often inherited from the org’s `.github` repo) are defined in:

- [31-repo-requirements.md](./31-repo-requirements.md)

### `README.md` (minimum)

Your `README.md` should answer, in the first screen:

- What does this do?
- Who is it for?
- What tier is it, and what expectations should users have?
- How do I try it in 5 minutes?
- Where do I file issues / ask questions?

Recommended extras that pay off quickly:

- A tier badge and a one-line support statement (so users can self-assess risk).
- A short “Status / Roadmap” section (even if it’s just 3 bullets).

### `LICENSE` (minimum)

Use the program’s default license unless you have a compelling reason not to.

- Typical default: Apache-2.0
- If you include third-party code, be ready to add a `THIRD_PARTY_NOTICES` file (see [34-legal-and-licensing.md](./34-legal-and-licensing.md)).

### `pipeline.yaml` (minimum)

`pipeline.yaml` is the structured metadata file used for:

- Directory generation and discovery
- Tier signaling
- Ownership and support clarity
- Review cadence automation (where enabled)

The authoritative schema is `playbook/schemas/pipeline.schema.json`.
For more detail on how metadata powers discovery, see [40-directory-and-metadata.md](./40-directory-and-metadata.md).

#### Minimal `pipeline.yaml` for **Experimental**

```yaml
schema_version: "1.0"

project:
  name: "tool-example"
  tagline: null
  description: "A concise description of what this project does and why it exists."
  tier: "experimental"
  lifecycle:
    created: "2026-01-20"
    last_reviewed: null
    sunset_date: null

ownership:
  owner:
    name: null
    github: "your-github-handle"
    org: "MongoDB"

links:
  repo: "https://github.com/mongodb-pipeline/tool-example"
  docs: null
  homepage: null
  showcase: []

audience:
  intended_users: ["internal"]
  personas: []
  maturity_expectation: "Pre-1.0; safe for evaluation and prototypes."

support:
  statement: "Experimental: best-effort community support; no SLAs."
  channels:
    - type: "github-issues"
      url: "https://github.com/mongodb-pipeline/tool-example/issues"
  security_policy_url: null

release:
  versioning: "none"
  current_version: null
  release_artifacts: ["source"]
  compatibility:
    mongodb: []
    runtimes: []

compliance:
  license: "Apache-2.0"
  cla_required: true
  third_party_notices: null
  telemetry:
    present: false
    notes: null

retirement:
  status: "active"
  message: null
  alternatives: []
```

#### Minimal `pipeline.yaml` for **Incubating**

```yaml
schema_version: "1.0"

project:
  name: "framework-example"
  tagline: null
  description: "A concise description of what this project does and why it exists."
  tier: "incubating"
  lifecycle:
    created: "2026-01-20"
    last_reviewed: "2026-01-20"
    sunset_date: null

ownership:
  owner:
    name: null
    github: "your-github-handle"
    org: "MongoDB"
  maintainers:
    - name: null
      github: "second-maintainer-handle"
      org: "MongoDB"

links:
  repo: "https://github.com/mongodb-pipeline/framework-example"
  docs: "https://github.com/mongodb-pipeline/framework-example#readme"
  homepage: null
  showcase: []

labels:
  areas: ["framework"]
  keywords: []

support:
  statement: "Incubating: best-effort support; breaking changes possible with notice."
  channels:
    - type: "github-issues"
      url: "https://github.com/mongodb-pipeline/framework-example/issues"
  security_policy_url: "https://github.com/mongodb-pipeline/framework-example/blob/main/SECURITY.md"

release:
  versioning: "semver"
  current_version: "0.1.0"
  release_artifacts: ["source"]
  compatibility:
    mongodb: ["7.0+", "8.0+"]
    runtimes: []

compliance:
  license: "Apache-2.0"
  cla_required: true
  third_party_notices: null
  telemetry:
    present: false
    notes: null

retirement:
  status: "active"
  message: null
  alternatives: []
```

If your `pipeline.yaml` doesn’t validate, treat that as a feature: it’s enforcing clarity.

## Open an intake issue (get listed + get eyes)

Open an intake issue once the repo has the minimum viable contract above.
This creates an audit trail and is typically how your repo gets picked up for listing/review.

Preferred (if your org has it):

- File an issue in the `intake` repo using the “Propose a project” issue form.

Fallback (if no `intake` repo exists yet):

- Open an issue in the `playbook` repo titled `Intake: <repo-name>` and include:
  - Repo URL
  - Proposed tier
  - One-sentence problem statement
  - Owner + maintainers
  - Any “review needed” flags (legal, security, branding)

For the full lifecycle and decision states, see [30-intake-process.md](./30-intake-process.md).

## First release checklist (minimal)

You should be able to do the following within your first 1–2 sessions:

- Build/run works from a clean checkout (document it in `README.md`).
- CI runs at least one “sanity” workflow (lint/test/build) appropriate for the language.
- A tagged release exists if you’re `incubating` (even if it’s `0.1.0`).
- Issues are enabled and have at least:
  - `bug`
  - `enhancement`
  - `help wanted` / `good first issue` (when relevant)

For deeper guidance, see [32-release-and-maintenance.md](./32-release-and-maintenance.md).

## Publish your first showcase update

The goal of a first showcase update is to make your project discoverable and to set expectations.

Minimum “good” first post:

- What you built and why (1–2 paragraphs)
- Who should try it (personas / use cases)
- Current tier + what that means
- A 5-minute quickstart or demo link
- What you need next (feedback, adopters, contributors)
- A short roadmap (3–5 bullets)

See [41-showcase-program.md](./41-showcase-program.md) for what qualifies and how often to post.
