# Framework Overview

**Purpose:** Explain the model, not the details.

The MongoDB Pipeline exists to make it easy to build in public, learn quickly, and give users clear expectations about the maturity and support level of each project.

## Why an incubator

An incubator helps us do three things consistently:

- **Capture innovation signals:** field-built or community-adjacent tooling can be valuable long before it becomes a product.
- **Move faster in public:** small, high-leverage ecosystem bets (frameworks, integrations, AI tooling) benefit from rapid iteration and early feedback.
- **Create legitimate discovery:** a single org-level “home” makes projects findable and reduces confusion about “is this real?” and “should I depend on it?”

## What this is (and isn’t)

This framework is:

- A lightweight, GitHub-native operating model for incubating projects with clear tiers and expectations.
- A way to standardize **minimum viable governance** so builders can ship without heavy process.
- A discovery and storytelling system (directory + showcase) that makes progress visible.

This framework is not:

- An Open Source Program Office (OSPO). It does not attempt to centralize all open source policy, procurement, or compliance across the company.
- A promise that every project is production-grade or supported indefinitely.
- A monorepo. “Self-contained in the org” means consistent structure and centralized discovery, not “all code in one repo.”

## Who can propose projects

Initially, projects can be proposed by **internal MongoDB team members**. Contributions from external developers to accepted repos are welcome via the normal GitHub PR flow, subject to the repo’s contribution requirements.

Eligibility and the intake steps are defined in `playbook/docs/30-intake-process.md`.

## The core contract: clarity of expectations

Every incubated project must make the following obvious to a user within a minute:

- What it does and who it’s for (`README.md`)
- What tier it is, and what that implies (`pipeline.yaml` + README tier badge/support statement)
- Where support happens (issues/discussions and a support statement)
- Whether it is actively maintained (metadata “last reviewed” signals, releases, and recent updates)

Repo requirements are defined in `playbook/docs/31-repo-requirements.md`.
Metadata and discovery are defined in `playbook/docs/40-directory-and-metadata.md`.

## How the framework works (high level)

At a high level, the pipeline is a lifecycle with consistent artifacts:

1. **Build:** start from a template (or create a repo) and add minimum required files.
2. **Describe:** add `pipeline.yaml` so the directory can discover and classify the repo.
3. **Intake:** open an intake issue so the project can be reviewed and accepted into the program.
4. **Ship:** publish small releases and keep the repo healthy (issues, docs, basic CI).
5. **Broadcast:** publish periodic showcase updates so users can follow along.
6. **Decide:** promote, continue incubating, or retire based on evidence and fit.

Builder workflow: `playbook/docs/01-quickstart-for-builders.md`.
Steering committee workflow: `playbook/docs/02-quickstart-for-steering-committee.md`.

## What lives where (org-level building blocks)

The framework is designed to be “self-contained” within a GitHub organization:

- **`.github`**: org-wide defaults and baseline policies (issue/PR templates, shared workflows).
- **`playbook`**: the rules of the road (this documentation).
- **`templates`**: “start here” repository templates for new projects.
- **`intake`**: a GitHub-native workflow for submissions, decisions, and audit trail (issues + labels + project board).
- **`directory`**: the machine-readable registry of projects (built from each repo’s `pipeline.yaml`).
- **`showcase`**: subscribable progress updates (launches, deep dives, adoption stories).

Naming conventions and additional structure guidance: `STRUCTURE.md`.

## Tiers at a glance

Tiers are how we communicate maturity and expected risk:

- **Experimental:** rapid iteration; minimal stability guarantees; “safe to evaluate”.
- **Incubating:** gaining traction; clearer compatibility expectations; stronger hygiene and security posture.
- **Supported:** a product-aligned ownership model exists; exits incubation to a long-term home.
- **Retired:** archived with a clear explanation and alternatives.

Full expectations per tier live in `playbook/docs/11-tiers-and-expectations.md`.

## Promotion, demotion, and exit (at a glance)

Projects change tiers based on evidence and readiness, not time spent in the org.

- Promotion and demotion criteria and required artifacts: `playbook/docs/12-promotion-and-demotion.md`
- How “Supported” works and what it means to exit incubation: `playbook/docs/13-supported-projects-and-exit.md`

## Governance (at a glance)

Governance is intentionally minimal:

- Builders own their repos and ship quickly.
- A steering committee provides periodic review, recommendation, and spotlighting.
- Decisions are documented in GitHub (issues, labels, and meeting notes), so the program stays transparent and auditable.

Governance model: `playbook/docs/20-governance-model.md`.
Roles: `playbook/docs/21-roles-and-responsibilities.md`.
Cadence and health checks: `playbook/docs/22-review-cadence-and-health.md`.

## Directory and showcase (why both exist)

- The **Directory** is the machine-readable registry of what exists, who owns it, and what tier it’s in.
- The **Showcase** is the narrative layer: launch posts, updates, deep dives, and “request for contributors.”

Directory: `playbook/docs/40-directory-and-metadata.md`.
Showcase program: `playbook/docs/41-showcase-program.md`.
Spotlighting and promotion content: `playbook/docs/42-spotlighting-and-promotion-content.md`.

## What success looks like (high level)

Success is measured by:

- More useful projects being created and made discoverable.
- Faster feedback loops (adopters, issues, PRs) and clearer signals on what to invest in.
- Increased ecosystem credibility: users can see what’s active, what’s experimental, and what’s supported.
- Stronger contributor funnel: internal builders recognized and external contributions enabled.

Metrics and evidence guidance:

- `playbook/docs/50-success-metrics.md`
- `playbook/docs/51-promotion-evidence-guide.md`
