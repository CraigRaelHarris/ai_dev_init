# [Project name]

[One sentence describing the client problem and intended outcome.]

## Status
Discovery captured; implementation has not started.

## Proposed stack
- ASP.NET Core API in C#.
- React with TypeScript and Vite.
- SQLite through Entity Framework Core.
- Exact SDK/package versions to be agreed during planning and pinned when scaffolded.

## Documents
- DISCOVERY.md: client facts, workflows, constraints and open questions.
- SCOPE.md: MVP boundaries, success measures and acceptance examples.
- DECISIONS.md: agreed choices and reasons.
- docs/INTEGRATIONS.md: external systems and mock requirements.
- docs/PLAN.md: implementation sequence, populated after planning.
- docs/SETUP.md: setup checklist and commands to complete after scaffolding.
- docs/CLINE-START.md: first Plan-mode prompt.
- .clinerules/project.md: persistent project instructions.

## Proposed structure
- src/Api: backend, EF Core migrations and configuration.
- src/Web: frontend.
- tests/Api.Tests: backend tests.
- docs: project documentation.
- data: local runtime database, ignored by Git.

## Run and verify
Not yet scaffolded. Cline must add exact restore, migration, seed, run, build,
lint, type-check and test commands to docs/SETUP.md after implementation.

## Configuration
Use .NET User Secrets for backend development credentials.
React variables are public; never put credentials in VITE_ variables.
The frontend .env.example is a copyable template. The backend configuration
example must be reviewed and placed in src/Api when the API is scaffolded.
