**Purpose:** Explain how discovery works
**Sections:**

* Why `pipeline.yaml` exists
* Required fields vs optional fields
* Tier-specific required metadata
* How the directory gets generated
* How to update metadata safely


Sample:

```yaml
schema_version: "1.0"

project:
  name: "framework-spring-session-mongodb"
  tagline: "MongoDB-backed Spring Session store"
  description: "A Spring Session implementation backed by MongoDB, intended for modern Spring Boot apps."
  tier: "incubating" # experimental | incubating | supported | retired
  lifecycle:
    created: "2026-01-10"
    last_reviewed: "2026-01-15"
    sunset_date: null

ownership:
  owner:
    name: "Alex Bevilacqua"
    github: "alexbevi"
    org: "MongoDB"
  maintainers:
    - name: "Jane Doe"
      github: "janedoe"
      org: "MongoDB"
  sponsor_pm: # required only for supported
    name: null
    github: null

links:
  repo: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb"
  docs: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/blob/main/README.md"
  homepage: null
  showcase:
    - title: "Initial release + roadmap"
      url: "https://github.com/mongodb-pipeline/showcase/blob/main/posts/2026/01/spring-session-mongodb.md"

labels:
  areas: ["framework", "java", "spring"]
  keywords: ["session", "spring-boot", "mongodb"]

audience:
  intended_users: ["internal", "external"] # internal | external | both
  personas: ["app-dev", "platform-eng"]
  maturity_expectation: "Pre-1.0 API; safe for evaluation and pilots."

support:
  statement: "Incubating: best-effort community support; no SLAs."
  channels:
    - type: "github-issues"
      url: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/issues"
    - type: "discussions"
      url: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/discussions"
  security_policy_url: "https://github.com/mongodb-pipeline/framework-spring-session-mongodb/blob/main/SECURITY.md"

release:
  versioning: "semver" # semver | date | none
  current_version: "0.3.0"
  release_artifacts: ["source"] # source | docker | npm | maven | pypi | rubygems | other
  compatibility:
    mongodb: ["6.0+", "7.0+", "8.0+"]
    runtimes: ["Java 17+", "Spring Boot 3.2+"]

compliance:
  license: "Apache-2.0"
  cla_required: true
  third_party_notices: true
  telemetry:
    present: false
    notes: "No telemetry planned."

signals:
  internal_adoption:
    customer_zero_team: "Internal Engineering"
    known_consumers: ["IE Platform Team"]
    known_instances: 2
  community:
    stars: null
    forks: null
    contributors_external: null

retirement:
  status: "active" # active | deprecated | archived
  message: null
  alternatives: []
```