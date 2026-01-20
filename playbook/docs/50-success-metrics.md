# Success Metrics

**Purpose:** Define what you measure and why.

Metrics exist to keep the incubator honest: are we accelerating useful ecosystem work, creating adoption signals, and improving user trust?

This doc covers:

- **Program-level metrics** (how the incubator is performing overall)
- **Project-level signals** (how an individual repo is performing)
- **Customer Zero signals** (internal engineering usage as an early indicator)

Tier changes use evidence, not just numbers. See `playbook/docs/12-promotion-and-demotion.md`.

## Principles (how to use metrics)

- Prefer **trend** over absolute counts (MoM / QoQ).
- Combine **quantitative** and **qualitative** signals.
- Avoid vanity metrics as sole decision drivers (stars ≠ adoption).
- Keep measurement lightweight; don’t burden builders with heavy reporting.
- Use metrics to **reduce user risk** (health/maintenance posture), not to punish builders.

## Program-level metrics

These measure the effectiveness of the pipeline as a system.

### Portfolio growth and activity

- New repos onboarded (MoM)
- Repos by tier (Experimental / Incubating / Supported / Retired)
- Projects with a current heartbeat (`project.lifecycle.last_reviewed` within policy)

Health policy: `playbook/docs/22-review-cadence-and-health.md`.
Metadata contract: `playbook/docs/40-directory-and-metadata.md`.

### Showcase and narrative output

- New showcase entries published (MoM)
- Showcase cadence compliance for Incubating/Supported (e.g., “has posted in last 90 days”)
- Spotlight features shipped (if you run a spotlighting program)

Showcase program: `playbook/docs/41-showcase-program.md`.

### Community and contribution funnel

- New contributors (internal vs external) across all repos (MoM)
- Total PRs merged and issues closed (MoM)
- Time-to-first-response on issues (portfolio-level median)

### Promotion and graduation outcomes

- Promotions (Experimental→Incubating; Incubating→Supported) per period
- Successful exits to a long-term home (Supported exit outcomes)
- Retirements with clear alternatives (portfolio hygiene)

Supported/exit: `playbook/docs/13-supported-projects-and-exit.md`.

## Project-level signals

These are signals the owner can use to decide: keep iterating, seek contributors, promote, demote, or retire.

### Adoption and usage

Good signals include:

- Known internal consumers and workflows enabled (“Customer Zero”)
- Downstream references (docs, blog posts, other repos)
- Repeat usage patterns (e.g., “used in 3+ teams”)

If you can measure usage safely and ethically, consider:

- package downloads (npm/pypi/maven)
- Docker pulls (if published)

### Engagement and contribution

Useful signals:

- Issues opened with real use cases (not just “it doesn’t work”)
- PRs from new contributors
- External questions and discussions that indicate adoption intent

### Maintenance health

Signals that matter for user trust:

- CI green on default branch
- Releases published and `release.current_version` kept current
- Time-to-first-response consistent with the stated tier/support posture
- `project.lifecycle.last_reviewed` kept current

## Customer Zero signals (Internal Engineering)

Internal Engineering is the early proving ground. Signals that indicate “this is worth investing in”:

- The project reduced meaningful developer friction (less boilerplate, faster delivery).
- The project is used in a repeatable way (multiple services/teams).
- The project unblocks ecosystem presence (framework/AI integration that would otherwise default elsewhere).

Concrete indicators:

- Named internal teams using it
- Documented internal adoption story (showcase entry)
- Demonstrated “enabled solutions” count (how many projects/solutions it powered)

Showcase adoption stories: `playbook/docs/41-showcase-program.md`.

## Where signals live (recommended)

Keep signals close to the project and machine-readable when possible:

- `pipeline.yaml` `signals` block (free-form; program can standardize later)
- Showcase posts (adoption stories, progress updates)
- Issues/PRs (public evidence trail)

Metadata: `playbook/docs/40-directory-and-metadata.md`.

## Notes on tooling (Common Room, telemetry, etc.)

Tooling is optional. Use it only if it reduces manual work and respects privacy/security constraints.

- Community analytics tools (e.g., Common Room) can help track GitHub engagement and contributor growth.
- Driver-level telemetry hooks (where applicable and approved) can provide usage signals, but must be:
  - transparent to users
  - compliant with policy and consent expectations
  - documented in `pipeline.yaml` under `compliance.telemetry`

Security considerations: `playbook/docs/33-security-and-responsible-disclosure.md`.
Legal considerations: `playbook/docs/34-legal-and-licensing.md`.

## How metrics influence decisions (quick mapping)

- **Promote to Incubating:** evidence of real users + maintenance posture + compatibility clarity.
- **Promote to Supported:** strategic fit + committed ownership (Sponsor PM) + reliable releases.
- **Demote:** the project cannot meet the promises of its tier.
- **Retire:** unmaintained or misleading; provide alternatives and document the decision.

Decision process: `playbook/docs/12-promotion-and-demotion.md`.
