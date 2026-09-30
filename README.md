# AI Development Project Starter

A documentation-first starter kit for defining and delivering small AI-assisted
client solutions safely. It helps a team turn an initial request into a
measurable, testable vertical slice before generating application code.

The template is designed for use with an AI coding assistant such as Cline or
Kilo Code. It keeps business requirements, technical decisions, integration
boundaries, evaluations, and guardrails in the repository as durable project
context.

## Status

This repository contains planning templates and example configuration only. It
does not contain a scaffolded or runnable application.

## What This Starter Enforces

- Validate the business problem before selecting an AI solution.
- Define a measurable outcome, baseline, target, and method of measurement.
- Map the current workflow, including exceptions and manual handoffs.
- Assign an authoritative source for every important fact.
- Separate probabilistic AI work from deterministic business rules.
- Define permitted autonomy, approvals, audit requirements, and safe failures.
- Deliver one thin end-to-end workflow before expanding the solution.
- Test normal, invalid, duplicate, unavailable, ambiguous, and adversarial cases.

## Proposed Stack

The project template starts with the following proposal, which should be
validated against the client's requirements during planning:

- ASP.NET Core API in C#
- React with TypeScript
- SQLite with Entity Framework Core
- OpenAPI for the HTTP contract and Postman compatibility

Exact SDK and package versions are intentionally left open until planning. Pin
them when the application is scaffolded.

## Repository Layout

```text
.
|-- README.md       # This starter-kit overview
|-- spec.md         # Discovery and completeness principles
|-- notes.md        # Maintainer notes and reference commands
`-- root/           # Files to place at the root of a new client project
    |-- README.md
    |-- DISCOVERY.md
    |-- SCOPE.md
    |-- DECISIONS.md
    |-- config/
    |   |-- appsettings.Development.example.json
    |   `-- web.env.example
    `-- docs/
        |-- CLINE-START.md
        |-- EVALS.md
        |-- GUARDRAILS.md
        |-- INTEGRATIONS.md
        |-- PLAN.md
        `-- SETUP.md
```

## Document Guide

| File | Purpose |
| --- | --- |
| `DISCOVERY.md` | Records the client problem, workflow, users, data, constraints, facts, assumptions, and open questions. |
| `SCOPE.md` | Defines the MVP boundary, first complete workflow, success measures, acceptance examples, and definition of done. |
| `DECISIONS.md` | Captures proposed and agreed technical or product decisions with their tradeoffs. |
| `docs/INTEGRATIONS.md` | Describes authoritative systems, API behavior, mocks, failure handling, and manual exception work. |
| `docs/GUARDRAILS.md` | Defines tool permissions, approval rules, data protection, prompt-injection defenses, and recovery behavior. |
| `docs/EVALS.md` | Defines representative AI evaluation cases, scoring, release gates, and evidence to retain. |
| `docs/PLAN.md` | Holds the agreed design, delivery sequence, verification checks, progress, and blockers. |
| `docs/SETUP.md` | Tracks prerequisites, configuration practices, scaffolding requirements, and tested commands. |
| `docs/CLINE-START.md` | Provides the initial Plan-mode prompt and project setup requirements for the coding assistant. |
| `config/` | Contains non-secret backend and frontend configuration examples. |

## Start a Project

1. Create an empty project directory and initialize a Git repository.
2. Copy the contents of `root/` into the new project's root, preserving hidden
   files and directories if present.
3. Complete `DISCOVERY.md` with confirmed facts, anonymized examples,
   assumptions, and owned open questions.
4. Draft `SCOPE.md`, `docs/INTEGRATIONS.md`, `docs/GUARDRAILS.md`, and
   `docs/EVALS.md` with project-specific details.
5. Record known choices and tradeoffs in `DECISIONS.md`.
6. Review the example configuration files without adding secret values.
7. Configure the coding assistant, required provider, approval settings, and
   only the tools needed for the project.
8. Commit the completed discovery baseline.
9. Open `docs/CLINE-START.md` and use its prompt in Plan mode.
10. Review and approve the resulting plan before allowing application code to
    be generated.

The expected flow is:

```text
Discover -> Scope -> Decide -> Plan -> Scaffold -> Verify -> Build -> Evaluate
```

## Delivery Sequence

The first implementation should remain deliberately small:

1. Scaffold the API, frontend, and test projects.
2. Verify that the API starts, the frontend builds and loads, and migrations can
   create a fresh local database.
3. Add repeatable development seed data.
4. Implement one complete workflow using agreed mocks where necessary.
5. Verify acceptance examples, failure handling, guardrails, and evaluations.
6. Connect real integrations only after access and side effects are approved.
7. Replace template placeholders with exact, tested run and deployment commands.

## Configuration and Secrets

- Keep backend development credentials in .NET User Secrets or an equivalent
  secret store, never in committed configuration.
- Treat all React `VITE_` variables as public and never place credentials in
  them.
- Use the files under `root/config/` as placeholders, not production-ready
  configuration.
- Keep local databases, generated output, dependencies, and sensitive files out
  of Git.
- Use synthetic or anonymized data until handling of real client data has been
  explicitly approved.

## Definition of Ready to Build

Planning is ready to move into implementation when:

- The business problem, named users, and measurable target are explicit.
- A normal journey and high-risk exceptions have acceptance examples.
- Sources of truth and behavior for conflicting or missing data are documented.
- The MVP boundary and excluded work are agreed.
- Integration mocks, failures, retries, duplicates, and human handoff are
  specified.
- Data access, tool permissions, approvals, audit, and fallback behavior are
  defined.
- Open questions have owners, due dates, and known consequences.
- The first checkpoint is a useful end-to-end vertical slice.

## After Scaffolding

The new project's README and `docs/SETUP.md` must be updated with verified
commands for dependency restoration, configuration, database migration and
seeding, startup, build, linting, type checking, tests, and evaluations. Include
working directories, ports, expected URLs, and any requirement for separate
terminals. Until those commands have been tested against generated application
code, they should not be documented as working commands.
