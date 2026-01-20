# Review Cadence and Health

**Purpose:** Prevent zombie repos without heavy process.

The goal of health checks is simple: keep the directory trustworthy and reduce user risk. A repo can be quiet and still be healthy, but it must not be misleading.

Governance context: `playbook/docs/20-governance-model.md`.
Role expectations: `playbook/docs/21-roles-and-responsibilities.md`.

## Required heartbeat

Every active repo (non-retired) must periodically prove it is still alive.

Recommended minimum heartbeat:

- **Incubating / Supported:** at least **quarterly** (every ~90 days)
- **Experimental:** at least **twice per year** (every ~180 days)

How to satisfy the heartbeat:

- Update `project.lifecycle.last_reviewed` in `pipeline.yaml` (preferred).
- Or, post a “still active” review comment in the repo’s health issue (if your program uses automation).

If you cannot meet the heartbeat, demotion or retirement may be recommended to avoid misleading users.

## Health signals (what we look at)

Health is assessed using a mix of signals. Not all signals apply to every project or tier.

### User trust signals (always relevant)

- `README.md` clearly states tier and support posture.
- Support channels exist and are accurate (issues/discussions links work).
- `pipeline.yaml` validates and reflects reality (owners, tier, links, last reviewed).

### Maintenance signals

- Issues and PRs receive responses consistent with tier expectations.
- CI is not persistently broken on default branch.
- Releases exist when expected for the tier (especially Incubating/Supported).

### Adoption and fit signals (informational)

- Internal adoption (“Customer Zero”) and known consumers.
- External interest (stars/forks, issues/PRs, downstream references).
- Strategic fit remains valid (still solving the right problem).

Tier expectations: `playbook/docs/11-tiers-and-expectations.md`.
Signals and metrics: `playbook/docs/50-success-metrics.md`.

## Health states

To keep process lightweight, health is treated as a small state machine:

- **Healthy:** meets heartbeat; signals consistent with tier.
- **Needs attention:** one or more signals are drifting (stale review date, slow triage, CI broken).
- **At risk:** repeated drift or non-responsiveness; user risk rising.
- **Recommend demotion/retirement:** repo is misleading users or effectively unmaintained.

## What happens when health degrades (warning → demotion → archive recommendation)

### 1) Warning / Needs attention

Triggered by:

- Heartbeat missed once.
- CI broken on default branch for an extended period.
- Issues/PRs not triaged in a way that matches the tier’s support statement.

Action:

- Steering committee (or automation) opens/updates a health issue with clear action items and a due date.

### 2) At risk

Triggered by:

- Heartbeat missed multiple times.
- Owner/maintainers are non-responsive to health issues.
- Security posture is unclear for Incubating+ (missing or incorrect security policy link).

Action:

- Steering committee requests a decision: add maintainers, demote tier, or propose retirement.

### 3) Demotion recommendation

Demotion is appropriate when the repo is still valuable but cannot meet the promises of its current tier.

Required changes (usually a single PR):

- Update `pipeline.yaml` tier and required fields for the new tier.
- Update `README.md` tier badge/support statement to match.
- Publish a short showcase update explaining the change (optional but recommended).

Process and criteria: `playbook/docs/12-promotion-and-demotion.md`.

### 4) Retirement recommendation (archive)

Retirement is appropriate when the repo is no longer maintained or would mislead users if left “active”.

Required changes:

- Follow deprecation guidance if appropriate (`retirement.status: deprecated` with message and alternatives).
- When archiving: set `project.tier: retired`, set `project.lifecycle.sunset_date`, set `retirement.status: archived`, and include `retirement.message` + `retirement.alternatives`.
- Add a prominent README banner and provide migration guidance.

Retirement guidance: `playbook/docs/11-tiers-and-expectations.md`.

## Automation expectations

Automation is optional but recommended for scale.

Suggested automation behaviors:

- Scheduled workflow opens a “Quarterly review due” issue per Incubating/Supported repo.
- Scheduled workflow flags repos with stale `project.lifecycle.last_reviewed`.
- Scheduled workflow flags repos with invalid `pipeline.yaml`.
- Health issues use consistent labels (e.g., `health:needs-attention`, `health:at-risk`).

If you’re implementing the directory and metadata pipeline, see `playbook/docs/40-directory-and-metadata.md`.

## Where health gets tracked (system of record)

Health tracking should be GitHub-native:

- Intake/health issues (single source of truth)
- Linked PRs for tier/metadata updates
- Steering committee decision record

Intake workflow: `playbook/docs/30-intake-process.md`.
Steering operations: `playbook/docs/02-quickstart-for-steering-committee.md`.
