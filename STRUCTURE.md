## How projects live in the org

### Naming conventions

* `ai-<thing>` (e.g., `ai-langchain-toolkit`)
* `framework-<thing>` (e.g., `framework-spring-session-mongodb`)
* `tool-<thing>` (e.g., `tool-schema-infer`)
* `sample-<thing>` (e.g., `sample-mastra-mongodb`)

### Standard repo requirements (enforced by Actions)

* Tier badge + support statement in README
* `pipeline.yaml` present and valid
* License + third-party notices (if needed)
* Security + reporting path
* Maintainers listed
* “Last reviewed” within N days (or it gets flagged)

## Governance, but GitHub-native

### Teams

* `steering-committee` (owners of playbook + intake)
* `maintainers` (general maintainer pool)
* `reviewers-legal` / `reviewers-security` (as-needed)
* `showcase-editors` (content support)

### Review cadence automation

* A scheduled workflow opens issues:

  * “Quarterly review due for <repo>”
  * “No showcase update in 90 days—still alive?”
* Steering committee uses the `intake` project board as the agenda.

## “Self-contained” doesn’t mean “one repo”

It means:

* **One org URL** people remember
* **One playbook** for rules
* **One intake** for decisions
* **One directory** for discovery
* **One showcase** for narrative + updates
* **Many projects** that follow the same contract

That gives you consistency without centralizing all code into a monorepo.

## What this looks like to a contributor (happy path)

1. Go to org home → click “Start a project”
2. Uses template repo → fills `pipeline.yaml`
3. Opens an “Intake: Propose project” issue (auto-linked)
4. Automation validates required files + tier badge + license
5. Steering committee accepts → project appears automatically in `directory` and `showcase`
6. Later, they PR a showcase update → it’s published + subscribers get notified
7. If traction grows, a “Promotion request” issue is filed with evidence

## Extra pieces that tend to be “meaningful” in practice

* **“Adopt me” / “Help wanted” labels** standardized across all repos
* **A “known gaps” backlog** in `intake` (field + PM signal aggregator)
* **A “starter kits” section** in Showcase (AI frameworks, templates, demos)
* **A “graduation playbook”** for moving a repo out of the incubator org cleanly
* **A lightweight trademark/branding guide** (what can use MongoDB marks)
