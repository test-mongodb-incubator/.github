# Intake Process

**Purpose:** How a project enters the pipeline.

Intake is the system of record for program decisions (acceptance, tiering, and early risk review). It keeps the directory trustworthy without creating a heavy approval board.

Builder happy path: `playbook/docs/01-quickstart-for-builders.md`.
Governance context: `playbook/docs/20-governance-model.md`.

## Eligibility (initially internal-only)

Initially, projects proposed for incubation are limited to:

- Projects proposed by **internal MongoDB team members** (owners/maintainers).

External developers are welcome to contribute to accepted repos via PRs, subject to the repo’s `CONTRIBUTING.md` and CLA expectations.

If/when external project onboarding becomes in-scope, this document should be updated to define:

- how external repos are evaluated
- who can propose them
- what trademark/branding rules apply

## The intake workflow (GitHub-native)

Intake should be tracked in a single, predictable place (typically an `intake` repo using issue forms + labels + a project board). If you don’t have an `intake` repo yet, use issues in `playbook` as a fallback.

### Step 0: Decide the initial tier

Choose between:

- **Experimental** (default; fastest path)
- **Incubating** (requires stronger hygiene and metadata)

Tier expectations: `playbook/docs/11-tiers-and-expectations.md`.

### Step 1: Create the repo

- Create from an org template if available (recommended).
- Add the minimum required files and `pipeline.yaml`.

Repo requirements: `playbook/docs/31-repo-requirements.md`.
Metadata: `playbook/docs/40-directory-and-metadata.md`.

### Step 2: Open an intake issue

Create an intake issue using the “Propose a project” form (recommended) or a structured issue template.

Minimum information to include:

- Repo URL
- Proposed tier (Experimental/Incubating)
- One-sentence problem statement and target users
- Owner and maintainers (GitHub handles)
- Primary support channel (issues/discussions link)
- Any flags requiring review: **security**, **legal/licensing**, **branding**, **duplication** (“does something like this already exist?”)

### Step 3: Triage

Steering committee (or designated triagers) reviews the submission and assigns one of:

- **Accept**
- **Request changes**
- **Defer**
- **Not accepted**

Operational decisioning: `playbook/docs/02-quickstart-for-steering-committee.md`.

### Step 4: Acceptance and listing

Once accepted:

- Ensure metadata validates for the tier.
- Ensure the repo’s README clearly states tier + support posture.
- The repo becomes eligible to appear in the directory/showcase pipelines.

If the project is accepted as Experimental but aspires to Incubating, capture the promotion criteria as action items.

Promotion guidance: `playbook/docs/12-promotion-and-demotion.md`.

## Triage criteria (how we decide)

Intake focuses on a small set of consistent criteria:

### 1) Fit

- Is this relevant to MongoDB’s ecosystem (frameworks, integrations, tooling, AI workflows, samples)?
- Does the project solve a real problem for intended users?
- Is the scope appropriate for incubation (not a one-off snippet; not an internal-only tool)?

### 2) Duplication

- Does an equivalent project already exist in the org (or upstream)?
- If yes, should this merge, contribute upstream, or reposition as an adapter/integration?

### 3) Risk

At intake we assess “obvious” risks:

- **Security:** is there a clear reporting path (`SECURITY.md` link)? Is the project handling sensitive data? Is it safe to publish?
- **Legal/licensing:** is the code safe to open source? any third-party code? license compatibility?
- **Reputation:** does the README set accurate expectations, or could users assume it’s supported when it’s not?

Security guidance: `playbook/docs/33-security-and-responsible-disclosure.md`.
Legal guidance: `playbook/docs/34-legal-and-licensing.md`.

### 4) Ownership

- Is there a clear owner and at least a plausible maintenance plan?
- For Incubating+, are there maintainers beyond a single person?

## Acceptance outcomes

### Accepted (Experimental)

Use when:

- The project is valuable to evaluate, but maintenance/stability promises are minimal.

Typical required changes (if any):

- Improve README clarity (tier + support statement + how to try).
- Ensure `pipeline.yaml` validates for Experimental.

### Accepted (Incubating)

Use when:

- The project already has users and a stronger hygiene posture.

Typical required changes (if any):

- Add maintainers
- Add security policy URL
- Add release metadata and compatibility expectations

### Request changes

Use when:

- The idea is acceptable, but the repo contract is incomplete (missing files, unclear tier, missing metadata/security link).

### Defer

Use when:

- Timing or focus is unclear, or overlap/strategy questions need resolution.

### Not accepted (+ guidance)

Use when:

- The project is out of scope, duplicative without clear differentiation, or too risky to publish.

Provide a next-best alternative:

- contribute upstream instead
- publish as a blog post or sample snippet
- keep internal-only (if appropriate)

## Fast path (strategic areas)

Some areas may justify expedited acceptance (e.g., AI tooling, high-leverage framework integrations), but the baseline contract remains:

- honest tier signaling
- minimum required repo files
- valid `pipeline.yaml`

Fast path should still record a decision in the intake issue and capture follow-ups (security link, docs, first release).
