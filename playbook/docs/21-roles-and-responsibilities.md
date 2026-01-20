# Roles and Responsibilities

**Purpose:** “Who does what” in one page, with clear escalation paths.

This framework is designed so builders can move quickly without ambiguity. Roles are defined to protect users (clear expectations) and reduce operational friction.

For tier expectations, see [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
For the intake workflow, see [30-intake-process.md](./30-intake-process.md).

## Project Owner

**Primary responsibility:** the project exists and stays honest about its tier and support posture.

Responsibilities:

- Own the project direction and roadmap (or explicitly state non-goals).
- Ensure `README.md` clearly states tier, support statement, and “how to try it”.
- Keep `pipeline.yaml` accurate and schema-valid for the current tier.
- Recruit/maintain a maintainer set appropriate for the tier.
- Participate in health reviews and respond to steering committee requests.
- Drive promotions/demotions/retirement decisions (with steering recommendation).

Time expectations:

- Experimental: periodic engagement, enough to keep the repo truthful.
- Incubating+: ongoing triage and predictable release posture.

Escalation path:

- If the owner is non-responsive, escalate to the steering committee per [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).

## Maintainers

**Primary responsibility:** keep the repo usable, responsive, and secure relative to its tier.

Responsibilities:

- Triage issues and review/merge PRs.
- Maintain CI health and basic build/run instructions.
- Publish releases consistent with the tier’s expectations.
- Handle security reports per `SECURITY.md` and program guidance.
- Update compatibility docs (MongoDB/runtime/framework versions) as needed.

Time expectations:

- Incubating+: maintainers should be able to respond to issues/PRs regularly and keep CI green.
- Supported: maintainers should support predictable releases and SemVer change management.

Escalation path:

- If maintainer capacity is insufficient, propose demotion or additional maintainers via intake.

## Contributors

**Primary responsibility:** follow the repo’s contribution guidance and help improve the project.

Responsibilities:

- Follow `CONTRIBUTING.md` (tests, style, sign-off/CLA if required).
- Use issues/discussions to propose changes before large PRs.
- Respect tier posture: Experimental code may churn; Supported may require stricter change management.

Time expectations:

- No fixed expectations; contributions are voluntary.

Escalation path:

- If blocked, use issues/discussions; if process issues persist, raise to steering committee via intake.

## Sponsor PM (Supported projects)

**Primary responsibility:** ensure “Supported” reflects durable ownership and an exit plan, not just a label.

Responsibilities:

- Validate strategic fit and document the “why” for ongoing investment.
- Ensure there is a long-term ownership model beyond the original builder.
- Help define and track success signals (adoption, ecosystem value).
- Partner on the exit plan to a durable org/team home and ensure it happens.
- Participate in steering reviews when Supported status or major tier changes are considered.

Time expectations:

- Ongoing light-touch involvement; heavier during promotion-to-supported and exit execution.

Escalation path:

- If a Supported project loses product alignment or ownership, coordinate with steering to demote or retire as appropriate.

Exit and supported definition: [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md).

## Steering Committee

**Primary responsibility:** maintain the program contract and keep the directory trustworthy.

Responsibilities:

- Triage intake submissions and record outcomes.
- Review and recommend tier changes and retirements based on evidence and health.
- Assign Sponsor PMs for Supported candidates.
- Maintain program assets (playbook, templates, directory conventions, showcase guidance).
- Handle escalations (non-responsive owners, security/reputational risk).

Time expectations:

- Meet every 6–8 weeks (or as defined) plus async review for urgent items.

Escalation path:

- For high-risk decisions, involve security/legal reviewers as appropriate.

Operational handbook: [02-quickstart-for-steering-committee.md](./02-quickstart-for-steering-committee.md).
Governance model: [20-governance-model.md](./20-governance-model.md).

## DevRel / PMM (spotlighting and promotion content)

**Primary responsibility:** help tell the story and amplify projects without changing the support contract.

Responsibilities:

- Partner with owners on showcase posts and technical narratives.
- Help define content themes (launch posts, updates, deep dives, adoption stories).
- Maintain editorial standards so posts are clear, accurate, and aligned with tier expectations.
- Coordinate spotlighting for strategically important projects.

Time expectations:

- As-needed; typically tied to spotlighting cycles and major releases.

Escalation path:

- If a project’s public messaging conflicts with its tier/support posture, coordinate with steering and the owner to correct it.

Showcase guidance: [41-showcase-program.md](./41-showcase-program.md).
Spotlighting guidance: [42-spotlighting-and-promotion-content.md](./42-spotlighting-and-promotion-content.md).

## Quick escalation matrix

- **Owner unresponsive / repo stale:** [22-review-cadence-and-health.md](./22-review-cadence-and-health.md) → steering committee review.
- **Tier change request:** [12-promotion-and-demotion.md](./12-promotion-and-demotion.md) → intake issue + evidence packet.
- **Supported exit needed:** [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md) → Sponsor PM + steering tracking.
- **Security concern:** [33-security-and-responsible-disclosure.md](./33-security-and-responsible-disclosure.md) → follow `SECURITY.md`.
