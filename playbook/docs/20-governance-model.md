# Governance Model

**Purpose:** Minimum viable governance rules: low friction, clear accountability, and a trustworthy directory.

This framework is intentionally GitHub-native. Governance is designed to:

- Keep it easy for builders to ship.
- Make user expectations unambiguous (tiers + support posture).
- Prevent “zombie repos” without heavy bureaucracy.

For the operational “how we run meetings”, see `playbook/docs/02-quickstart-for-steering-committee.md`.
For role definitions, see `playbook/docs/21-roles-and-responsibilities.md`.
For tier definitions, see `playbook/docs/11-tiers-and-expectations.md`.

## Governance goals

This governance model optimizes for:

- **Speed with clarity:** projects move fast, but users can tell what’s safe to adopt.
- **Distributed ownership:** project owners make day-to-day decisions; governance focuses on the program-level contract.
- **Transparency by default:** decisions are recorded in GitHub issues, labels, and docs updates.
- **Evidence-based tier changes:** promotion/demotion decisions reference adoption and health signals.
- **Low ceremony:** minimal required artifacts; avoid heavyweight review boards unless necessary.

## Entities and scopes

### Project governance (per repo)

Each repo is owned and run by its maintainers. They control:

- Technical direction and roadmap
- Release cadence and compatibility posture
- Triage and contribution workflow
- Tier signaling in `README.md` and `pipeline.yaml`

### Program governance (the incubator)

Program governance exists to ensure consistency across repos:

- Enforce the baseline repo contract (required files, metadata validity, clarity of support).
- Provide periodic review and recommendations (promotion/demotion/retirement, spotlighting).
- Maintain the playbook, templates, directory, and showcase program.

## Steering committee

### Composition

The steering committee should include at least:

- **Engineering representation** (practical operational and technical review)
- **Product management representation** (strategy alignment and supported/exit path)
- Optional: **Developer Relations / PMM** as advisors for spotlighting and narrative

The goal is minimum viable governance, not a large committee.

### Responsibilities

The steering committee:

- Reviews intake submissions and records outcomes.
- Recommends promotion/demotion/retirement based on evidence and health signals.
- Identifies and assigns a Sponsor PM for projects proposed to become Supported.
- Maintains program artifacts:
  - playbook docs
  - templates
  - directory metadata conventions
  - showcase guidance
- Handles escalations for non-responsive ownership and risk concerns.

Intake process: `playbook/docs/30-intake-process.md`.
Tier change criteria: `playbook/docs/12-promotion-and-demotion.md`.

## Decision model

### Default decision states

For program decisions (intake, tier changes, spotlighting), outcomes are:

- **Accept**
- **Request changes**
- **Defer**
- **Retire recommendation**

These states are documented in `playbook/docs/02-quickstart-for-steering-committee.md`.

### Voting (lightweight)

By default, decisions should be made by **consensus** among the steering committee members present.

If consensus cannot be reached:

- A simple majority vote can be used for non-critical decisions.
- For high-risk decisions (security, legal, reputational), defer and escalate to the appropriate reviewers.

When in doubt, prefer **defer** with clear action items over a rushed decision.

### System of record

The system of record is GitHub:

- Issues (intake/promotion/retirement requests)
- Labels (state, tier, review needs)
- Linked PRs (metadata + docs updates)
- Meeting notes/minutes (if recorded)

## Escalation and conflict resolution

### Conflicts within a repo

Repos should resolve technical disagreements within their maintainer group. If a repo needs a decision rule, keep it simple (e.g., maintainer consensus; owner breaks ties).

### Conflicts affecting the program

Escalate to the steering committee when conflicts impact:

- Tier signaling and user trust
- Security posture or vulnerability handling
- Brand/reputational risk
- Ownership disputes that block maintenance

If unresolved, the steering committee can recommend demotion or retirement to reduce user risk.

## Transparency norms

Transparency is a feature of the program. At minimum:

- Tier changes and retirement decisions include public rationale (issue + showcase post).
- `pipeline.yaml` is kept current so the directory stays trustworthy.
- Health review outcomes are visible (issues or review comments).

Review cadence and health: `playbook/docs/22-review-cadence-and-health.md`.

## What governance does not do

To keep friction low, the steering committee does not:

- Approve every PR in every repo.
- Own day-to-day roadmap decisions for projects.
- Guarantee support, SLAs, or product commitments unless explicitly stated per project.
