# Promotion Evidence Guide

**Purpose:** Help owners assemble a promotion packet quickly.

Promotion decisions should feel predictable. This guide tells you what to collect, what “minimum bar” looks like, and how to write a promotion request that a steering committee can evaluate quickly.

Tier change process: `playbook/docs/12-promotion-and-demotion.md`.
Tier expectations: `playbook/docs/11-tiers-and-expectations.md`.
Metadata contract: `playbook/docs/40-directory-and-metadata.md`.
Repo requirements: `playbook/docs/31-repo-requirements.md`.

## What evidence matters (by transition)

Promotion is fundamentally about user trust:

- Are there real users?
- Can maintainers sustain the promises of the target tier?
- Is the project’s scope and strategy fit clear?

### Evidence categories (use what applies)

**Adoption**

- Named internal consumers (“Customer Zero” teams)
- External interest (issues, discussions, downstream references)
- Usage signals (downloads/pulls) where applicable

**Maintenance health**

- CI green and stable on default branch
- Releases published and versioning consistent with tier
- Issue/PR responsiveness consistent with stated support posture
- `project.lifecycle.last_reviewed` is current

**Clarity and usability**

- README has a 5-minute quickstart and clear “who it’s for”
- Compatibility expectations documented (MongoDB + runtimes/frameworks)
- Support channels are correct and discoverable

**Risk management**

- Security reporting path exists (required for Incubating+)
- Licensing is correct and third-party notices handled (if applicable)
- No obvious reputational risk from unclear messaging

Success signals reference: `playbook/docs/50-success-metrics.md`.

## Minimum bar: Experimental → Incubating

Incubating is where users start to depend on you. The minimum bar is “usable, maintained, and honest”.

### Required (must have)

- Real users (at least one internal team or a plausible external user group).
- At least two maintainers identified (not just one owner).
- Security reporting path in place (`SECURITY.md` and `support.security_policy_url`).
- A versioned release and compatibility expectations (MongoDB + runtime/framework).
- Current `project.lifecycle.last_reviewed`.

### Strong evidence (nice to have)

- A “Customer Zero” adoption story (showcase post).
- A small set of curated issues demonstrating real use cases.
- A roadmap with the next 1–2 milestones.

### Common reasons Incubating promotion gets deferred

- No maintainer capacity beyond the owner.
- Compatibility unclear (“which MongoDB versions does this support?”).
- No security policy link.
- Repo is not yet runnable/usable from docs.

## Minimum bar: Incubating → Supported

Supported implies durable ownership and a path out of the incubator org. The minimum bar is “strategically aligned, reliably maintained, and ready to be depended on”.

### Required (must have)

- Sponsor PM assigned and engaged (with GitHub handle in metadata).
- SemVer releases with a clear change management posture.
- Demonstrated adoption trajectory (internal and/or external).
- Clear support channels and responsiveness posture that matches “Supported”.
- Exit plan: where the repo will live long-term and who will own it.

Supported and exit guidance: `playbook/docs/13-supported-projects-and-exit.md`.

### Strong evidence (nice to have)

- Multiple internal teams using it (or strong external pull and usage).
- Stable API boundaries (few breaking changes; clear deprecation policy).
- Deep dive docs or a reference architecture that shows the project’s value.

### Common reasons Supported promotion gets deferred

- No Sponsor PM or unclear product alignment.
- Exit plan is missing or unrealistic.
- Release posture is not stable (no SemVer discipline, unclear compatibility).
- Ownership is still “single maintainer”.

## Promotion packet checklist (copy/paste)

Use this as a PR/issue checklist when requesting promotion.

- [ ] Link to repo
- [ ] Current tier and requested tier
- [ ] One-sentence problem statement and intended users
- [ ] Owner and maintainers (GitHub handles)
- [ ] Support statement and support channels
- [ ] Security policy URL (Incubating+)
- [ ] Releases and current version
- [ ] Compatibility expectations (MongoDB + runtimes/frameworks)
- [ ] Adoption evidence (Customer Zero teams and/or external signals)
- [ ] Health evidence (CI status, responsiveness, last reviewed date)
- [ ] Risks and mitigations (maintenance, security, licensing, overlap)
- [ ] If requesting Supported: Sponsor PM + exit plan details

## Example promotion request write-up

Use this structure in an intake issue (or the promotion request form).

**Title:** Promote `<repo-name>` to `<incubating|supported>`

**Summary**

- What it is: …
- Who it’s for: …
- Why now: …

**Requested tier and rationale**

- Current tier: …
- Requested tier: …
- What will be different for users after promotion: …

**Evidence**

- Adoption: …
- Maintenance health: …
- Releases/versioning: …
- Compatibility: …
- Security: …

**Risks**

- Top risks: …
- Mitigations: …

**Artifacts**

- PR link updating `pipeline.yaml` and `README.md`: …
- Showcase post link (or planned): …

**If Supported**

- Sponsor PM: …
- Exit plan (destination org, timeline, ownership): …
