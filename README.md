# The MongoDB Pipeline

`mongodb-pipeline/.github` (org-wide policy and defaults)

Why: Central place to enforce “minimum viable governance” and reduce friction.

Contains:

- [x] CODE_OF_CONDUCT.md (not https://www.mongodb.com/community-code-of-conduct)
  - [ ] describe means of reporting issues
- [ ] SECURITY.md
- [ ] SUPPORT.md (what “supported vs incubating” means in plain language)
- [x] CONTRIBUTING.md (org-wide contribution expectations)
- [ ] Issue templates (bug, feature request, showcase entry, promotion request, retirement request)
- [ ] PR templates (incl. “release readiness” checklist)
- [ ] Reusable workflows (license check, secret scan, required files check, metadata lint)

This is the “org contract”: every repo inherits the same baseline.

## Playbook

`mongodb-pipeline/playbook`

Why: This becomes your “single source of truth” playbook that anyone can link to.

## Templates

`mongodb-pipeline/templates`

Why: Make the happy path extremely fast: “copy template → ship something.”

What’s inside:

* Repo template(s) (GitHub “Use this template”):
  * template-experimental
  * template-incubating (adds more guardrails)
* Standard files:
  * README.md with tier badge + support statement
  * PROJECT.md (scope, non-goals, roadmap)
  * GOVERNANCE.md (maintainers, decision-making)
  * MAINTAINERS.md
  * LICENSE (Apache 2.0)
  * THIRD_PARTY_NOTICES.md template
  * docs/ skeleton
* GitHub Action workflow snippets:
  * required-file enforcement
  * release drafting
  * changelog automation
  * “metadata validator” (see directory section below)

Optional but powerful:
* Language-specific “starter modules” (Node/Go/Python/Ruby) that include:
* logging, telemetry hooks (where acceptable), CI, basic examples
* a consistent “MongoDB sample app” harness for adoption demos

## Intake 

`mongodb-pipeline/intake` (maybe if we want to propose projects)

Why: One predictable place for proposing projects, promotion, spotlighting, retirement.

How it works:
* GitHub Issues = submissions (with form templates)
  * “Propose a project for incubation”
  * “Request promotion”
  * “Request retirement”
  * “Request spotlight / showcase feature”
* GitHub Project board = state machine
  * New → Triage → In Review → Accepted → Live → (Promoted | Retired)
* Labels enforce taxonomy:
  * tier:experimental, tier:incubating, tier:supported, tier:retired
  * decision:needs-pm, decision:legal, decision:security
  * area:ai, area:framework, area:language, area:tooling

This becomes your operational heartbeat and audit trail.

## Directory

`mongodb-pipeline/directory` (machine-readable registry of everything)

Why: The “Showcase” and discovery UX get dramatically easier if every project is described in a structured way.

Core idea: every project repo contains a pipeline.yaml (or .mongodb/pipeline.yaml) with metadata, and directory aggregates them.

Example metadata fields:
* name, description, tier
* owner(s) + GitHub handles
* sponsor PM (if any)
* tags (ai, langchain, spring, rails, etc.)
* intended users (internal, external, both)
* “support statement” (one-liner)
* maturity signals (downloads, stars, internal adopters)
* “showcase URL(s)” (posts, demos)
* last-reviewed date

Directory repo content:
* /registry/ (collected metadata snapshots)
* /scripts/ (collector + validator)
* /docs/ (how the directory works)
* A generated README.md table + filters
* Optional: GitHub Pages site generated from the registry

## Showcase

Why: You want “subscribable, centralized, incremental updates” without needing a separate CMS. Could just be a Jekyll blog.

Two good patterns:

A) Markdown-first showcase (fastest)
* Each showcase entry = PR adding a markdown file:
  * /posts/YYYY/MM/project-name-update.md
* Use tags + frontmatter for filtering
* GitHub Discussions can mirror posts (“Release Update: …”)
* Atom/RSS via Pages (or just “Watch releases/discussions”)

B) Generated site (still all in GitHub)
* showcase repo hosts a static site (e.g., Docusaurus/MkDocs/Jekyll)
* CI pulls from directory registry + showcase posts
* Publishes to GitHub Pages under the org

Either way, “Showcase content” is a PR-based workflow with clear ownership and review.