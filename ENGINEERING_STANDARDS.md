# Engineering Standards
## Andrea Kwabena Technologies / AndieKobbieTech

**Status:** Baseline standard, proposed for adoption across first-party repositories  
**Snapshot date:** 25 November 2026  
**Owner:** Andie Kobbie  
**Canonical location:** GitHub profile repository

This document establishes a consistent engineering approach across personal and organisation-owned software projects. It is deliberately additive: it sets defaults for new work and gives existing projects a path to improve without forcing rewrites or erasing sound engineering decisions.

## 1. Purpose and scope

The standard applies to first-party products, services, libraries, SDKs, infrastructure repositories and maintained internal tools owned or controlled by Andrea Kwabena Technologies / AndieKobbieTech.

Classify each repository before applying requirements:

| Repository class | Treatment |
|---|---|
| First-party product or service | Apply the relevant baseline and product requirements. |
| Library, SDK or open specification | Apply package, compatibility, documentation, testing and release requirements. |
| Infrastructure / platform | Apply infrastructure, security, change-control and operational requirements. |
| Research or learning project | Apply proportionate documentation, reproducibility and safety requirements. |
| Upstream fork, mirror or vendor source | Preserve upstream conventions; do not impose unrelated refactors. Keep local changes isolated and documented. |
| Archived, superseded or legacy system | Do not migrate solely for consistency. Apply security fixes when justified and document support status. |
| Third-party course material | Preserve its educational purpose and attribution; do not represent it as first-party product engineering. |

A repository can have more than one class. Record the primary class and any important exceptions in its README or project documentation.

## 2. Non-negotiable principles

1. **Preserve working systems.** No mass rewrites, framework swaps, dependency churn or directory restructuring solely to match this document.
2. **Fit the technology to the problem.** The preferred stack is a default, not a mandate to use Django for every workload.
3. **Make changes reviewable.** Prefer small, scoped pull requests with tests and clear rollback paths.
4. **Protect compatibility.** Preserve public APIs, data formats, URLs, user workflows and integrations unless a deliberate versioned change is approved.
5. **Make security observable.** Record dependency, build, test and release evidence appropriate to the repository's risk.
6. **Document reality.** Distinguish implemented, tested, planned, experimental and deprecated capabilities.
7. **Keep ownership clear.** Organisation-owned systems and sensitive project data remain under the relevant organisation's control.

## 3. Preferred application stack

### 3.1 Default for new full-stack products

For a new, domain-rich web application where a conventional backend is justified:

| Layer | Preferred default | Use |
|---|---|---|
| Primary language | Python | Application logic, automation, AI integrations and backend services. |
| Backend framework | Django | Domain models, authentication, permissions, administration and server-rendered or API-backed applications. |
| REST API | Django REST Framework (DRF) | Default for conventional REST APIs, serializers, permissions and browsable API workflows. |
| Typed API alternative | Django Ninja | Use where typed schemas and OpenAPI-first ergonomics are a better fit. Do not add both DRF and Ninja without a documented reason. |
| Frontend | React + TypeScript | Interactive product interfaces, dashboards and complex client-side workflows. |
| Relational database | PostgreSQL | Default durable relational store for production applications. |
| UI build tooling | Vite | Default for a React single-page application where a separate backend serves the API. |
| Containers | Docker / Compose | Reproducible local development and portable service packaging. |
| Infrastructure as code | Terraform | Repeatable cloud infrastructure where infrastructure is managed as code. |
| Observability | OpenTelemetry | Traces, metrics and logs where service complexity or operational risk warrants it. |

Use currently supported stable releases at project inception, pin dependencies through the repository's chosen lockfile, and upgrade deliberately.

### 3.2 Framework selection is contextual

- **Django** is the default when the product needs a coherent domain model, relational persistence, authentication, permissions, admin workflows and a mature application framework.
- **FastAPI** remains appropriate for independent asynchronous services, model-serving APIs and small service boundaries where Django's application layer would add unnecessary weight.
- **Django Ninja** and **DRF** are alternatives for API design, not a requirement to run two API frameworks in every Django project.
- **Hono / Cloudflare Workers** remain appropriate for edge-native services and products whose existing architecture depends on Workers, Durable Objects or platform-native execution.
- **Node.js / TypeScript** remains appropriate for existing JavaScript services, SDKs, browser tooling and runtimes where the ecosystem is a better fit.
- **Rust, Go, Java, C# and PHP** remain valid where performance, systems integration, existing ownership, platform constraints or project maturity justify them.
- **Static HTML, Astro, Decap CMS or another static-first approach** remains preferable for content sites that do not need a permanent application backend.

### 3.3 CMS and content architecture

Choose the lightest content system that meets the editorial requirement:

- **Wagtail** for a Django-backed editorial platform with structured content, permissions and publishing workflows.
- **Decap CMS** for Git-backed content editing on static sites.
- **Static content / Markdown** where editing workflows are simple and a CMS would add unnecessary operational cost.

Do not introduce a database-backed CMS merely to provide an admin interface. Do not replace a working CMS without a documented user, operational or security benefit.

### 3.4 Python project conventions

For new Python packages and services:

- Declare project metadata and dependencies in `pyproject.toml`.
- Prefer `uv` for new environments and lockfiles unless a runtime or deployment platform requires another tool.
- Use `pytest` for automated tests.
- Use `ruff` for linting and formatting unless an established project has a justified alternative.
- Add static type checking proportionate to the public API and complexity.
- Keep optional integrations and development dependencies separate.
- Publish libraries with semantic versioning, changelogs and reproducible build metadata.

Existing Poetry, pip, setuptools and other working project setups are not to be migrated simply for uniformity.

### 3.5 TypeScript project conventions

For new React applications:

- Use TypeScript strict mode.
- Keep the package manager and lockfile consistent; never commit multiple competing lockfiles without a documented reason.
- Use the existing test framework where established; Vitest is the default for new Vite projects.
- Separate UI state from server state and centralise API access.
- Validate untrusted input at system boundaries.
- Keep shared API contracts typed and test compatibility when changing them.

Existing Bun, npm, pnpm and Yarn projects retain their established toolchain unless there is a specific, measured reason to change it.

## 4. Architecture and maintainability

Every maintained product repository should have, proportionate to its size:

- A README explaining purpose, status, prerequisites, setup, verification and deployment.
- A clear source-of-truth for configuration and environment variables.
- A documented boundary between frontend, backend, infrastructure and shared contracts.
- Tests for critical behaviour and regression-prone paths.
- Architecture Decision Records (ADRs) for consequential decisions, migrations and non-obvious trade-offs.
- A changelog or release notes for versioned products and libraries.
- A contribution guide and security contact/process for public projects.

Use modular monoliths by default when they keep deployment and operations simpler. Introduce services, queues, event buses or microservices only when independent scaling, fault isolation, team boundaries or integration requirements justify them.

Do not split a system into services just to make its architecture look more advanced.

## 5. Security, dependencies and software supply chain

Apply controls according to exposure, data sensitivity and operational criticality.

### 5.1 Baseline for maintained repositories

- Never commit real credentials, tokens, private keys, production data or personal data.
- Provide safe placeholders in `.env.example`; exclude real local environment files.
- Keep dependency manifests and lockfiles committed.
- Review dependency changes and remove unused or unmaintained packages.
- Use Dependabot or an equivalent updater for ecosystems that the repository actually uses.
- Enable secret scanning and push protection where available; use a repository-appropriate secret scanner in CI where practical.
- Add a `SECURITY.md` with a responsible disclosure route for public software.
- Use least-privilege workflow permissions and avoid exposing secrets to untrusted pull-request code.

### 5.2 CI security and supply-chain evidence

For maintained deployable applications, libraries and services, progressively adopt:

- Dependency review on pull requests.
- CodeQL or an appropriate SAST tool for supported languages.
- Container image scanning where containers are built or published.
- An SBOM in CycloneDX or SPDX format, generated from the actual resolved dependencies.
- Build and test evidence attached to releases.
- Provenance or signed release artefacts where the distribution and risk justify it.

An SBOM must be generated from the build or resolved dependency graph, not maintained as a manually edited inventory. If an SBOM is checked into the repository, document how and when it is regenerated so it cannot silently become stale.

Do not add every scanner to every repository. Select tools that understand the languages and deployment model in use, and avoid workflows that produce permanent noise without an owner.

### 5.3 Dependabot policy

For eligible maintained repositories:

- Enable updates for the package ecosystems present.
- Start with a weekly schedule; group compatible patch and minor updates where that reduces review noise.
- Keep major upgrades individually reviewable.
- Include GitHub Actions and container ecosystems where relevant.
- Do not create update configuration for ecosystems the repository does not use.

### 5.4 Data protection

Use synthetic or anonymised fixtures in tests and demonstrations. Keep sensitive personal, beneficiary, client and operational data in approved organisation-controlled systems. Logs, telemetry, screenshots and AI prompts must not become an accidental secondary data store.

## 6. Testing and delivery

A change should run the checks relevant to the files and behaviour it touches.

| Project type | Typical verification |
|---|---|
| Python library / service | pytest, lint, type check, package build |
| Django application | Django system checks, migrations check, pytest, API and permission tests |
| React / TypeScript | lint, type check, unit/component tests, production build |
| Infrastructure | formatting, validation, policy checks, plan review and controlled apply |
| Containerised service | application tests, image build and image scan |
| Cross-service integration | contract tests, integration tests and failure-path checks |

For production-facing repositories, CI should provide a repeatable minimum path from a clean checkout to a verified build. Do not claim a build or test passes unless it has actually been run.

Use separate environments for development, test, staging and production where appropriate. Production migrations and infrastructure changes must be deliberate, reviewable and recoverable.

## 7. Git and review workflow

Use short-lived branches and scoped pull requests.

| Branch prefix | Purpose |
|---|---|
| `feat/` | New functionality |
| `fix/` | Bug or regression fix |
| `docs/` | Documentation |
| `refactor/` | Internal restructuring without intended behaviour change |
| `chore/` | Maintenance and tooling |

Use Conventional Commit-style messages where practical: `type(scope): description`.

A pull request should explain:

- What changed and why.
- Which repositories, interfaces or data flows are affected.
- Tests and checks performed, including anything not run.
- Security, dependency and migration implications.
- Rollback or recovery considerations for operational changes.

Use branch protection and required checks on important shared repositories where the organisation's plan and permissions support them. Never force-push or rewrite shared history as a routine repair mechanism.

## 8. Operational readiness

For deployed services, document:

- How to configure and deploy the service.
- Health and readiness checks where applicable.
- Where logs, metrics and traces can be inspected.
- Backup and restore expectations for persistent data.
- How to roll back an application or schema change.
- External dependencies and known service limitations.
- Who owns the system and how incidents are escalated.

Prefer structured logs and OpenTelemetry instrumentation when they provide useful operational evidence. Do not add telemetry that captures secrets, prompts or personal data without an explicit and justified data-handling design.

## 9. Migration and exception policy

This standard is not a rewrite programme.

Before changing an existing project:

1. Classify the repository and identify its current runtime, dependencies, deployment path and users.
2. Record the concrete problem the change solves.
3. Check existing tests, documentation, CI, data formats and integrations.
4. Prefer an adapter or incremental boundary over a replacement.
5. Make the change on a dedicated branch and preserve the previous working path.
6. Add tests and migration notes; validate backwards compatibility.
7. Provide a rollback or recovery route.
8. Update the repository's documentation only where the behaviour or operating instructions actually change.

An exception is acceptable when it is technically justified. Record the reason in an ADR or the repository README. A project should not adopt Django, React, PostgreSQL, Docker or any other preferred tool if doing so makes that project less reliable or harder to maintain.

## 10. Adoption levels

| Level | Meaning | Minimum expectation |
|---|---|---|
| 0 — Experimental | Prototype, learning or research | Purpose, status, safe configuration and reproducible basic setup. |
| 1 — Maintained | Actively developed first-party repository | README, lockfiles, tests, CI, dependency updates and secret hygiene. |
| 2 — Production-facing | Deployed service or product | Level 1 plus security scanning, operational documentation, backup/rollback and release evidence. |
| 3 — Critical / sensitive | Handles sensitive data or supports important services | Level 2 plus documented access controls, data lifecycle, incident response, SBOM and stronger release/change controls. |

Do not label a repository production-ready simply because it has a deployment workflow or a polished README.

## 11. Initial ecosystem audit snapshot

The following figures were gathered on 25 November 2026 from the connected GitHub account and its available code-search index. They are a baseline for follow-up work, not a claim that every repository has been exhaustively inspected.

### Access and inventory

- The repository-list operation returned 100 personal-account repository records: 85 public and 15 private.
- The connected GitHub App exposed one installation, on the personal account `andiekobbietks`.
- The connected account's organisation-membership lookup returned no organisation memberships.
- The repository listing did not provide a complete inventory of all code-search results. These 100 records must not be used as the denominator for ecosystem-wide percentages.

### Indexed technology evidence

| Search evidence | Distinct repositories surfaced | Interpretation |
|---|---:|---|
| `src/main.tsx` | 41 | Strong existing React/Vite-style footprint. |
| `vite.config.ts` | 53 | Broad Vite configuration footprint; includes different project types. |
| `pyproject.toml` | 9 | Python packaging and project metadata are already present. |
| `requirements.txt` | 14 | Additional Python dependency manifests. |
| `package.json` | 19 | At least 19 repositories surfaced in the first 100 matching file results; large monorepos contribute multiple hits. |
| `manage.py` | 3 | Three repositories surfaced, but two contain Django-generation references rather than a verified Django runtime. |
| Django runtime imports and project files | 1 | One Django starter application was verified; its README says it is not production-ready. |
| `django-rest-framework` search | 0 | No indexed DRF match surfaced in this search. |

Search counts are lower-bound observations from indexed results. They can include forks, mirrors, prototypes, documentation references and multiple files in one repository. They are not a full language census, do not establish maintenance status, and must not be converted into adoption percentages.

### Existing controls and exemplars

- AgentSON already has Python packaging, a test suite, CI references, changelog and architectural/workflow documentation.
- AK Build has detailed repository-specific agent instructions, explicit architecture boundaries and separate type-check, lint, test and build commands.
- Windows-MCP has an actual Dependabot configuration.
- Taskmaster Productivity Suite contains CycloneDX SBOM and security documentation.
- Other repositories surface security documentation, CodeQL references and SBOM work.

These existing controls should be retained and used as reference patterns.

### Organisation access gap

The connected integration did not return Getaway AI or other organisation memberships. One public repository was surfaced under Irene Vera Foundation: `Irene-Vera-Foundation/ireneverafoundation-cms-wp`. Its README describes Roots Bedrock / WordPress, so it has not been assumed to be the separate Wagtail project. No organisation-wide audit or changes can be claimed until the relevant organisation repositories are visible through an authorised GitHub connection.

## 12. Next implementation sequence

1. Complete the organisation access review and build a full repository inventory.
2. Classify first-party repositories, forks, mirrors, learning projects and archived work.
3. Select representative first-party repositories for a detailed baseline review.
4. Apply the maintained-repository baseline to suitable projects in small pull requests.
5. Pilot the Python + Django + React/TypeScript stack on a genuinely new or suitable application, not by rewriting established products.
6. Track adoption by repository class, with verified numerator and denominator, and publish updated figures only after inventory completion.

**The target is a coherent engineering ecosystem, not a uniform codebase.** Python, Django and React/TypeScript become the preferred application-development path for new suitable products; existing technologies remain first-class where they serve their projects better.
