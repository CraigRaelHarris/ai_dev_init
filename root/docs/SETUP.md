# Setup

## Before planning
1. Extract these files into the project root, preserving hidden files/folders.
2. Replace placeholders in DISCOVERY.md and SCOPE.md; add anonymised examples.
3. Open the root folder in VS Code and trust its contents.
4. Install Git, the agreed .NET SDK and Node.js LTS compatible with the chosen frontend tooling.
5. If needed, install C# Dev Kit, ESLint and Prettier; optionally a SQLite viewer.
6. Verify `git --version`, `dotnet --info`, `node --version`, `npm --version`.
7. Initialise Git if needed, configure author identity and create a private remote.
8. Configure Cline's provider/model and enable the workspace rule.
9. Review auto-approval settings; connect only required MCP tools.
10. Commit the starter files and push when ready.
11. Start with docs/CLINE-START.md in Plan mode.

## During scaffolding
- Create src/Api, src/Web and tests/Api.Tests.
- Pin the installed agreed SDK in global.json and record Node requirements.
- Commit generated package lockfiles; use reproducible package installation.
- Add EF Core SQLite and design packages compatible with the chosen EF version.
- Use a repository-local EF tool manifest with a matching dotnet-ef version.
- Configure frontend `/api` development proxy and backend routes consistently.
- Configure a stable SQLite path and an ignored runtime data directory.
- Add shared VS Code run/debug tasks once actual project paths are known.
- Configure ESLint/Prettier and useful package scripts in the generated frontend.

## Backend configuration
Review config/appsettings.Development.example.json and merge the non-secret
settings into src/Api/appsettings.Development.json after scaffolding.
Resolve the relative database path against the API content root in code.
The sample path assumes src/Api is the content root.

Use `dotnet user-secrets init --project src/Api` after the API exists, then store
required development secrets with User Secrets. Do not commit their values.
ASP.NET Core does not load .env automatically; explicitly add a loader only if
needed. The backend example uses standard ASP.NET Core configuration instead.

## Frontend configuration
Copy config/web.env.example to src/Web/.env.example when scaffolded.
Prefer same-origin `/api` through the Vite proxy locally. All VITE_ values are
public. Never store backend API keys in React configuration.

## Commands to complete after scaffolding
Cline must replace this section with tested commands for:
- Backend/frontend dependency restore.
- Database migration and development seed.
- API and frontend startup, including ports.
- VS Code debugging and combined startup.
- Backend tests; frontend build, lint, type checks and relevant tests.
- Production configuration, persistent SQLite storage and backup/restore.

No application code is included in this starter pack.
