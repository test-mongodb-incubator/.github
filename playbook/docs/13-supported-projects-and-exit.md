# Supported Projects and Exit

**Purpose:** Define “Supported” and how a project leaves the incubator organization.

In this framework, **Supported** is not “the final tier inside the incubator.” It is an **exit ramp** to a long-term home with product-aligned ownership.

If you’re looking for tier definitions and user expectations, start with `playbook/docs/11-tiers-and-expectations.md`.

## What “Supported” means (and what it doesn’t)

### Supported means

- Users can reasonably treat the project as a long-lived dependency.
- Ownership is committed and explicit (maintainers + a Sponsor PM).
- Releases are versioned with SemVer and change management is predictable.
- There is an intent and plan to move the project out of the incubator into a durable org/team home.

### Supported does not mean

- A blanket promise of SLAs or enterprise support (unless explicitly stated in the repo’s support channels).
- That the incubator org becomes the permanent home for the repo.
- That the project is immune to retirement; it can still be deprecated/retired if strategy or viability changes.

## Supported tier requirements (schema-aligned)

When a project is marked `supported`, `pipeline.yaml` must satisfy the Supported rules in `playbook/schemas/pipeline.schema.json`, including:

- `ownership.maintainers` present
- `ownership.sponsor_pm.github` present
- `project.lifecycle.last_reviewed` present
- `release.versioning: semver`
- `release.current_version` present

See `playbook/docs/40-directory-and-metadata.md` for how metadata is used for discovery.

## Sponsor PM responsibilities

The Sponsor PM is accountable for helping the project exit incubation safely and sustainably.

Minimum responsibilities:

- Confirm the project aligns with a product direction or ecosystem strategy (and document the “why”).
- Ensure there is an ownership model beyond the original builder (maintainers + reviewers).
- Help define success metrics and the adoption story (internal “Customer Zero” and/or external).
- Partner on the exit plan: target org/home, timeline, and risks.
- Ensure the project has a clear maintenance posture (triage expectations, release cadence, compatibility story).

Governance expectations: `playbook/docs/20-governance-model.md`.
Review cadence and health checks: `playbook/docs/22-review-cadence-and-health.md`.

## Maintainer and owner responsibilities (Supported)

Supported maintainers should be able to commit to:

- Predictable releases and compatibility documentation.
- Issue/PR triage that matches the communicated support posture.
- Security intake and disclosure path (even if it’s “report via SECURITY.md and we will respond”).
- Change management: clear deprecation/breaking-change notes and migration guidance.

Release guidance: `playbook/docs/32-release-and-maintenance.md`.
Security guidance: `playbook/docs/33-security-and-responsible-disclosure.md`.

## Ownership transfer checklist (before exit)

Before relocating the repo, verify:

- **Ownership**
  - At least two maintainers are listed and have demonstrated activity.
  - Sponsor PM is named and reachable.
  - Decision-making and escalation path is documented (even if lightweight).
- **User trust**
  - README clearly states “Supported” and links to support channels.
  - Compatibility expectations are documented (MongoDB + runtime/framework).
  - There is a migration/deprecation story for any known breaking changes.
- **Operational health**
  - CI is green on default branch.
  - Releases are tagged and versioned with SemVer.
  - Security policy exists and is linked from metadata.
- **Compliance**
  - License is correct and third-party notices are present if needed.
  - No internal-only references, secrets, or confidential docs are in the repo history.

Promotion requirements and process: `playbook/docs/12-promotion-and-demotion.md`.

## Repo relocation process (preserving history)

The goal is to preserve git history and avoid breaking consumers.

Recommended process:

1. **Select the destination**
   - Choose the long-term GitHub org/repo that will own the project after incubation.
   - Confirm who will administer the repo (teams/permissions) post-move.
2. **Prepare a move PR in the source repo**
   - Add a short “Moving” note in `README.md` (or a banner) with the planned destination and date.
   - Ensure `pipeline.yaml` is current and links/support channels are correct.
3. **Move the repository**
   - Use GitHub’s repo transfer/move so issues, PRs, releases, and history are preserved.
   - Verify redirects work from the old URL to the new one.
4. **Post-move validation**
   - Confirm default branch protections and CI secrets/workflows are intact.
   - Confirm release automation still works (tags, changelog, artifacts).
   - Confirm links in README, metadata, and docs all point to the new home.
5. **Update discovery and record**
   - Update the directory/metadata source of truth to point to the new repo URL.
   - Close out the promotion/exit issue with final links and decision record.

The exit decision should be recorded through the intake workflow (issues + labels), even if the work happens across multiple repos.
Intake workflow: `playbook/docs/30-intake-process.md`.

If a move is not possible immediately (org constraints, permissions), the repo can remain temporarily in the incubator, but it must:

- Keep `supported` signaling accurate (do not “fake” Supported).
- Have an explicit exit plan and target date recorded in the intake issue.

## Communication plan (showcase + README + release notes)

Every exit should include a small comms package so users aren’t surprised:

- **Showcase update**
  - Why it’s supported, what changed, where it lives now, and how to get help.
  - Any migration steps (if repo name changes, package name changes, etc.).
- **README update**
  - Prominent “Moved to …” section (or banner) for a period of time.
  - Updated support channels and ownership info.
- **Release notes**
  - If there are breaking changes during the transition, document them in the release notes and provide migration guidance.

Showcase guidance: `playbook/docs/41-showcase-program.md`.

## If the exit plan fails

If the project cannot secure committed ownership or a durable home:

- Consider demotion back to Incubating (or Experimental) to reduce implied promises.
- If unmaintained or strategically misaligned, follow the deprecation/retirement process.

Demotion/retirement criteria: `playbook/docs/12-promotion-and-demotion.md`.
Tier and deprecation guidance: `playbook/docs/11-tiers-and-expectations.md`.
