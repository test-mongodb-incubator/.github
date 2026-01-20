# Showcase Program

**Purpose:** Make “broadcast progress” a repeatable practice.

The showcase is the narrative layer of the pipeline. It turns projects into discoverable, subscribable updates without requiring a separate CMS.

Directory and metadata (what exists): [40-directory-and-metadata.md](./40-directory-and-metadata.md).
Tier contract (expectations): [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
Comms snippets: [06-comms-kit.md](./06-comms-kit.md).

## What qualifies as a showcase entry

A showcase entry is any update that helps users answer:

- What does this project do?
- Is it active, and what’s changed?
- Who should use it (and who shouldn’t)?
- What help do the maintainers need?

Good entries are:

- **Honest** about tier, support posture, and current limitations.
- **Actionable** (include a quickstart/demo link and clear next steps).
- **Specific** (what shipped, what’s next, what you learned).

## How showcase ties back to metadata

Showcase posts should be linkable from the directory:

- Add each post under `links.showcase[]` in the project’s `pipeline.yaml`.
- Keep `links.docs` pointing at the best “start here” docs (often the README).

Directory/metadata contract: [40-directory-and-metadata.md](./40-directory-and-metadata.md).

## Cadence expectations

Cadence should match tier and activity, but avoid “silent repos” that look abandoned.

Recommended minimum cadence:

- **Incubating / Supported:** at least one showcase update every ~90 days while active.
- **Experimental:** at least one showcase update every ~180 days while active (or a clear status note in README).

If a project is not actively progressing, publish a short status update (“paused”, “seeking maintainers”, “deprecated”, etc.) so users aren’t guessing.

Health/heartbeat context: [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).

## Showcase entry types

Use the smallest post that accomplishes the goal.

### Launch post

Use when introducing a new repo to the program.

Must include:

- Problem statement and intended users
- Tier and support statement
- 5-minute quickstart
- Current limitations / non-goals
- How to give feedback or contribute

### Progress update

Use for incremental changes (monthly/quarterly).

Recommended structure:

- What changed (bullets)
- What you learned (1–2 bullets)
- What’s next (3–5 bullets)
- Where you want help (issues to tackle)

### Technical deep dive

Use for high-leverage docs:

- architecture decisions
- integration guides (frameworks/AI/tooling)
- performance considerations and tradeoffs

### Adoption story (“Customer Zero”)

Use when an internal team adopts the project.

Include:

- What workflow it enabled
- What would convince others to adopt
- Known constraints

### Call for contributors

Use when you need help to keep momentum:

- good first issues
- maintainer help
- docs/testing help

Comms copy/paste: [06-comms-kit.md](./06-comms-kit.md).

## Where it publishes

Pick one primary location; avoid splitting attention.

Common patterns:

- **A dedicated `showcase` repo** with Markdown posts (ideal for PR-based publishing).
- **GitHub Pages** generated from the `showcase` repo (optional).
- **GitHub Discussions** used to mirror posts (optional).

Regardless of where the content lives:

- Add the post URL to `pipeline.yaml` under `links.showcase[]` so the directory can link to it.
- Keep the repo’s README updated with “Latest update” links for fast scanning.

## Submission and review workflow (recommended)

Make publishing easy:

1. Author opens a PR adding a Markdown file in the `showcase` repo.
2. Optional editorial review by DevRel/PMM (“showcase editors”).
3. Merge → publish → subscribers get notified.

If you use an `intake` repo/project board, you can track showcase items as lightweight issues:

- “Showcase: Launch <repo>”
- “Showcase: Q1 update for <repo>”

Intake workflow: [30-intake-process.md](./30-intake-process.md).
Roles (DevRel/PMM): [21-roles-and-responsibilities.md](./21-roles-and-responsibilities.md).

## Subscription model

The program should be subscribable without extra tooling:

- Watch the `showcase` repo for releases/PR merges (or use GitHub notifications).
- Watch GitHub Discussions if posts are mirrored there.
- Optionally provide RSS/Atom via GitHub Pages.

## Quality bar (keep it light)

Avoid over-polishing. A “good enough” showcase update:

- is accurate about tier and support posture
- includes at least one link to try it
- names what changed and what’s next

If you need higher leverage content (e.g., spotlighting), see [42-spotlighting-and-promotion-content.md](./42-spotlighting-and-promotion-content.md).
