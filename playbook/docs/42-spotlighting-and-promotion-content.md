# Spotlighting and Promotion Content

**Purpose:** How to turn projects into awareness assets without violating the tier/support contract.

Spotlighting is “high signal” content: it helps the right users find the right project, and it can accelerate adoption and contributor interest. It should never make a project appear more supported than it is.

Tier contract: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).
Showcase basics: [41-showcase-program.md](./41-showcase-program.md).

## Spotlight criteria (what’s compelling)

Spotlight a project when one or more of these is true:

- It solves a common ecosystem pain (framework integration, language gap, AI workflow tooling).
- It has clear adoption signals (internal “Customer Zero”, growing external engagement).
- It introduces a reusable pattern others can replicate (templates, reference architectures).
- It is strategically aligned and timely (e.g., important AI/framework ecosystem moments).
- It is at a decision point (promotion to Incubating/Supported, or major new release).

Signals and metrics guidance: [50-success-metrics.md](./50-success-metrics.md).
Showcase publishing workflow: [41-showcase-program.md](./41-showcase-program.md).

## What spotlighting should always include

To keep trust high, every spotlight should explicitly state:

- Tier and support statement (and what that means)
- Intended users and non-users (“who this is for / not for”)
- Compatibility expectations (MongoDB versions, runtimes/frameworks as relevant)
- How to try it quickly (demo/quickstart)
- Where to get help (issues/discussions/security policy link)

Metadata and discovery: [40-directory-and-metadata.md](./40-directory-and-metadata.md).
Repo requirements: [31-repo-requirements.md](./31-repo-requirements.md).

## Content templates

These templates are intentionally short and PR-friendly. Use the smallest one that works.

### Template A: Short spotlight (200–400 words)

Use for:

- minor release highlights
- quick “why this matters” posts

Outline:

- One-sentence takeaway
- What it does (2–3 bullets)
- Tier + support statement (one line)
- Quickstart link + “try this” in 1–2 steps
- Call to action (feedback, contributors, adopters)

### Template B: Medium spotlight (600–900 words)

Use for:

- first serious adoption story
- meaningful new capability

Outline:

- Problem → solution summary
- Who it’s for / not for
- How it works (high level)
- Getting started (5 minutes)
- Tier + expectations + compatibility notes
- What’s next (roadmap bullets)
- How to contribute / where to ask questions

### Template C: Deep dive (1200+ words)

Use for:

- reference architectures
- framework integration guides
- performance/reliability tradeoffs

Outline:

- Context and problem framing (why now)
- Architecture diagram/description
- Key decisions and tradeoffs
- Security and operational notes
- End-to-end example
- Migration guidance (if replacing alternatives)
- Roadmap and contributor asks

Comms copy/paste and snippets: [06-comms-kit.md](./06-comms-kit.md).

## Approval and publishing flow (recommended)

Keep approvals lightweight and focused on messaging accuracy:

- **Owner + maintainer review:** technical accuracy, links, quickstart correctness.
- **DevRel/PMM editorial review (optional but recommended for spotlights):** clarity, audience fit, tier/support language, consistency.
- **Steering committee visibility (as needed):** if the spotlight coincides with promotion/demotion or a strategic announcement.

Roles: [21-roles-and-responsibilities.md](./21-roles-and-responsibilities.md).
Steering operations: [02-quickstart-for-steering-committee.md](./02-quickstart-for-steering-committee.md).

## Promotion content (when tier is changing)

Tier changes should be accompanied by a small narrative update:

- What evidence justified the change
- What new expectations users should have
- What remains experimental / what might still break
- Any migration guidance if behavior changed

Tier change process: [12-promotion-and-demotion.md](./12-promotion-and-demotion.md).
Evidence packet guidance: [51-promotion-evidence-guide.md](./51-promotion-evidence-guide.md).
Intake workflow (system of record): [30-intake-process.md](./30-intake-process.md).

## Example outlines

### AI integration spotlight

Use when shipping an integration for an agent framework / RAG workflow / model tooling.

- The workflow it unlocks (1 paragraph)
- What MongoDB provides in the stack (vector search, schema, operational model)
- Minimal example (code snippet link + “run this” steps)
- Known limitations (model/tooling constraints, cost considerations, scaling notes)
- Tier + support posture + contribution asks

### Framework integration spotlight (e.g., Spring/Rails/Next.js)

- The developer pain being solved (sessions, auth, caching, migrations, local dev)
- How the integration works (adapter, plugin, starter template)
- Compatibility matrix (framework + MongoDB versions)
- Quickstart (copy/paste)
- Production notes (timeouts, pooling, deployment shape)
- Tier + support posture + roadmap
