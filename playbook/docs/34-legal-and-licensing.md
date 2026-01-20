# Legal and Licensing

**Purpose:** Practical, checklist-oriented legal guidance for publishing and maintaining pipeline repos.

This playbook is not legal advice. It exists to help builders avoid common pitfalls and know when to involve Legal.

Repo contract: `playbook/docs/31-repo-requirements.md`.
Release checklist: `playbook/docs/32-release-and-maintenance.md`.

## Default license: Apache 2.0

Unless there is a compelling reason to do otherwise, pipeline repos are licensed under:

- **Apache License 2.0** (`Apache-2.0`)

Your repo must include a `LICENSE` file with the full license text.

In `pipeline.yaml`, set:

- `compliance.license: "Apache-2.0"`

## Third-party code and notices

Third-party OSS is common and usually fine, but it must be handled transparently.

### Dependencies vs bundled code

- **Dependencies** (pulled via a package manager): usually do not require a notices file, but you must comply with their licenses.
- **Bundled code** (copy/paste, vendored directories, embedded assets, or shipping third-party source in-repo): more likely to require explicit attribution and notices.

When in doubt, assume bundling requires extra care.

### When to add `THIRD_PARTY_NOTICES`

Add a `THIRD_PARTY_NOTICES` (or `THIRD_PARTY_NOTICES.md`) file if you:

- Vendor third-party source code into the repo.
- Ship third-party assets (e.g., fonts, icons, models) with non-trivial license terms.
- Distribute compiled artifacts that embed third-party code requiring notices.

In `pipeline.yaml`, set:

- `compliance.third_party_notices: true`

If you do not bundle third-party code, you may set it to `false` or `null` depending on your program convention.

### Never include confidential or proprietary material

Do not publish:

- Internal-only documentation, internal URLs, internal code names
- Customer data, contracts, or internal tickets
- Credentials, tokens, or secrets (including in history)

## Trademarks and branding (do’s and don’ts)

The goal is to avoid confusing users about what is “official” and what is “incubated”.

### Do

- Use accurate tier signaling and support statements in README.
- Use clear phrasing like “MongoDB Pipeline project” or “incubated in the MongoDB Pipeline”.
- Use descriptive repo names that reduce confusion (see `STRUCTURE.md`).

### Don’t

- Imply official product support if the project is not a product-supported deliverable.
- Use MongoDB trademarks/logos in a way that suggests endorsement beyond the stated tier.
- Name packages in a way that appears to be an official driver/component unless that’s explicitly intended and approved.

If you need branding guidance for a high-visibility project, involve Legal/Brand early.

## CLA requirement reference

Most MongoDB open source repos require a Contributor License Agreement (CLA) or a similar contribution agreement.

Your `CONTRIBUTING.md` must clearly state:

- whether a CLA is required
- how contributors complete it (link to the canonical CLA process)

In `pipeline.yaml`, set:

- `compliance.cla_required: true` (or the program default)

If your org maintains a canonical CLA document, link to it from:

- the org-wide `.github/CONTRIBUTING.md` (preferred)
- and/or each repo’s `CONTRIBUTING.md`

## When to involve Legal

Involve Legal early if any of the following apply:

- You are not using Apache-2.0 (license exception).
- You plan to vendor or embed third-party code/assets with unclear licensing.
- The project touches trademarks/branding in a way that could confuse users.
- The project includes cryptography, security tooling, or sensitive data handling with higher compliance expectations.
- You suspect code history may include internal-only or confidential material.
- You plan to redistribute binaries, Docker images, or packaged artifacts with complex licensing implications.

When you involve Legal, include:

- repo URL (or draft repo)
- intended license
- list of bundled third-party components (if any) with links/licenses
- planned distribution channels (source only vs packages/images)

## Checklist (copy/paste)

Before making a repo public or publishing a release:

- [ ] `LICENSE` present and matches `compliance.license` in `pipeline.yaml`
- [ ] `CONTRIBUTING.md` states CLA expectations and links to the canonical process
- [ ] No internal-only references, confidential docs, or customer data
- [ ] No secrets (including commit history, as feasible)
- [ ] `THIRD_PARTY_NOTICES` added if bundling third-party code/assets
- [ ] README tier/support posture is explicit and accurate
