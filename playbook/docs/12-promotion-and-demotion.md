# Promotion and Demotion

**Purpose:** Canonical criteria + process for changing a project’s tier.

Tier changes exist to protect users and keep the directory trustworthy. They are based on **evidence and readiness**, not time-in-tier.

For tier definitions, see [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).

## Who decides (decision owners)

- **Project owner / maintainers** own the proposal, the evidence, and the implementation work (docs, metadata, releases).
- **Steering committee** reviews and records a recommendation (accept / request changes / defer / retire recommendation).
- **Supported** requires a **Sponsor PM** and an exit plan (see [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md)).

Operational details for steering review: [02-quickstart-for-steering-committee.md](./02-quickstart-for-steering-committee.md).
Governance model: [20-governance-model.md](./20-governance-model.md).
Review cadence and health checks: [22-review-cadence-and-health.md](./22-review-cadence-and-health.md).

## What triggers promotion consideration

Promotion should be considered when at least one of these is true:

- **Adoption is growing:** internal usage (“Customer Zero”) or external interest is becoming meaningful.
- **The surface area is stabilizing:** fewer breaking changes, clearer API boundaries, compatibility story emerging.
- **Maintenance posture is proven:** issues are triaged, releases are happening, CI is healthy.
- **Strategic fit is clear:** the project fills an ecosystem gap aligned with MongoDB’s priorities (frameworks, integrations, AI tooling).

Promotion is optional; staying Experimental can be correct for a long time.

## Evidence required (what matters)

Promotion is an evidence exercise. Evidence can be qualitative, quantitative, or both.

**Always required (any promotion)**

- Clear problem statement + intended users.
- Clear ownership (who responds, who reviews, who releases).
- A working “how to try it” path (docs or quickstart).
- Release and maintenance posture appropriate to the target tier.

**Helpful signals**

- Internal adoption: known teams using it, examples of use in real workflows.
- External interest: stars/forks, issues/PRs, community questions, downstream references.
- Health: recent activity, CI green, response to issues, documented roadmap.
- Fit: why this should exist as an incubated project (vs a one-off gist, a blog snippet, or an upstream contribution only).

Evidence guidance and a “promotion packet” template: [51-promotion-evidence-guide.md](./51-promotion-evidence-guide.md).
Signals and metrics: [50-success-metrics.md](./50-success-metrics.md).

## Target tier requirements (schema-aligned)

When you change tiers, your `pipeline.yaml` must validate against the schema for the **target tier** (`playbook/schemas/pipeline.schema.json`).

### Experimental → Incubating (minimum bar)

You are ready for **Incubating** when:

- There are real users (internal or external) and you expect continued adoption.
- You can publish versioned releases and state compatibility expectations.
- You can commit to basic security hygiene (a security policy URL) and ongoing triage.

Metadata requirements (high level; exact rules in schema):

- `ownership.maintainers` present (more than just the owner).
- `support.security_policy_url` present.
- `labels.areas` present.
- `project.lifecycle.last_reviewed` present.
- `release.current_version` and `release.compatibility` present.

### Incubating → Supported (minimum bar)

You are ready for **Supported** when:

- The project is strategically important and should be depended on long-term.
- A Sponsor PM is assigned and there is a plan to move the repo to a long-term home.
- Stability posture is strong enough to require SemVer and clearer change management.

Metadata requirements (high level; exact rules in schema):

- `ownership.sponsor_pm.github` present.
- `release.versioning` is `semver` and `release.current_version` present.
- `project.lifecycle.last_reviewed` present.

Supported is an “exit ramp”: see [13-supported-projects-and-exit.md](./13-supported-projects-and-exit.md).

### Any tier → Retired (minimum bar)

Retirement is appropriate when:

- The project is unmaintained, superseded, or no longer fits strategy.
- Continued visibility would mislead users about safety/support.

Metadata requirements (high level; exact rules in schema):

- `project.tier` set to `retired`.
- `project.lifecycle.sunset_date` present.
- `retirement.status` set to `archived`.
- `retirement.message` and `retirement.alternatives` present.

Deprecation sequencing guidance: [11-tiers-and-expectations.md](./11-tiers-and-expectations.md).

## What triggers demotion or retirement

Demotion/retirement should be considered when one or more conditions persist:

- **Non-responsive ownership:** no maintainer response to issues/PRs for an extended period.
- **Broken health baseline:** CI consistently failing, releases broken, docs unusable.
- **Security risk:** known issues with no remediation path, or unclear vulnerability reporting path.
- **No longer fits:** project has been superseded, upstream adopted the solution, or the ecosystem moved.
- **Stale signals:** no meaningful usage or progress and no clear next step.

Demotion/retirement is about reducing user risk, not punishing builders.

## Demotion notes (keeping the record accurate)

Demotion typically means “lower the promise,” not “erase history.”

- Keep `pipeline.yaml` accurate and schema-valid for the new tier; do not delete useful fields just to “make it smaller”.
- Update `README.md` so users immediately see the new tier and support posture.
- Consider setting `retirement.status: deprecated` if you’re discouraging new adoption but not archiving yet.

## Required artifacts for any state change

Every tier change must include these updates (usually in the same PR as the metadata change):

- **`pipeline.yaml` updated** (tier + required fields for target tier).
- **`README.md` updated** (tier badge + support statement + any required banners such as deprecation/retirement).
- **Showcase update** describing the change (promotion rationale or retirement/migration guidance).
- **Directory/discovery correctness**: links and support channels still accurate.

If you’re changing to (or from) Incubating/Supported, also review:

- [32-release-and-maintenance.md](./32-release-and-maintenance.md)
- [33-security-and-responsible-disclosure.md](./33-security-and-responsible-disclosure.md)
- [34-legal-and-licensing.md](./34-legal-and-licensing.md)

## The process (GitHub-native)

Use the intake workflow as the system of record (issues + labels + decision record).

1. **Open a request**
   - Promotion request (e.g., “Promote `repo-name` to Incubating”)
   - Demotion request (e.g., “Demote `repo-name` to Experimental”)
   - Retirement request (e.g., “Retire `repo-name`”)
2. **Assemble an evidence packet**
   - Link to usage/adoption signals, issues/PRs, releases, and compatibility docs.
   - Include risks and mitigations (especially security/maintenance).
3. **Prepare the change PR**
   - Update `pipeline.yaml` to satisfy the target tier.
   - Update `README.md` tier badge/support statement (and banners if needed).
   - Add or link a showcase post for the change.
4. **Steering review**
   - Reviewed in the next steering cadence (or via async review if urgent).
   - Outcome recorded in the request issue.
5. **Execute and announce**
   - Merge the change PR.
   - Publish the showcase update and ensure directory metadata is accurate.

Intake workflow details: [30-intake-process.md](./30-intake-process.md).
Directory and metadata mechanics: [40-directory-and-metadata.md](./40-directory-and-metadata.md).
Showcase expectations: [41-showcase-program.md](./41-showcase-program.md).

## Fast path (strategic areas)

Some areas (for example: AI tooling, framework integrations, high-leverage language ecosystem work) may justify faster iteration and expedited decisions. A “fast path” should still include:

- Clear tier signaling (no ambiguity for users)
- Security reporting path if Incubating+
- A minimal evidence packet (who uses it, why now, what’s the next milestone)

## Common outcomes

- **Accept**: tier change approved; merge the PR.
- **Request changes**: gaps identified (usually metadata, docs, security policy, or release posture).
- **Defer**: not enough evidence yet; action items defined; revisit at next cadence.
- **Retire recommendation**: steering recommends deprecation/retirement; owner executes or committee escalates per governance.
