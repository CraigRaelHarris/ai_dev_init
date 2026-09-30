# Cline pre-plan
1. Create folder
2. Exit Restricted Mode
3. Init Git
4. Extract files into project root
5. fill in 
		DISCOVERY.md
		SCOPE.md
		docs/INTEGRATIONS.md
		DECISIONS.md
		README.md
		.clinerules/project.md
		docs/EVALS.md
		docs/GUARDRAILS.md
6. Configure Cline: provider, model, credentials, approval settings. Connect necessary MCP tools
7. Commit, push

# PLAN
8. use docs/CLINE-START.md

# ACT
9. Scaffold 
10. Verify that the API starts, React loads and migration creates the database 

# PLAN->ACT 
11. Add business features

--------------

# Tools
https://www.tablesgenerator.com/mediawiki_tables

# Files 
.clineignore								Excludes sensitive and generated files from Cline
.editorconfig								Consistent formatting
.gitignore									Excludes secrets, builds, dependencies and SQLite files
!!! DECISIONS.md							Decisions and reasons
!!! DISCOVERY.md							Client requirements, facts, assumptions and questions
!!! README.md								Project overview and document index (incl. recommended folder structure)
!!! SCOPE.md								MVP boundaries, acceptance examples and definition of done
!!! .clinerules/project.md					Cline instructions for this stack. Small project rules file. Include stack items. includes secrets handling. API error consistency
.vscode/extensions.json						Recommended extensions
.vscode/settings.json						Shared editor settings
config/appsettings.Development.example.json	Backend configuration example
config/web.env.example						Public frontend configuration example
docs/CLINE-START.md							First Plan-mode prompt
!!! docs/EVALS.md							representative inputs, expected behaviour, scoring criteria, pass thresholds and regression checks.
!!! docs/GUARDRAILS.md						permitted actions, data/tool access boundaries, prompt-injection handling, output validation, human approval and fallback behaviour.
!!! docs/INTEGRATIONS.md					APIs, mocks and manual exception handling
docs/PLAN.md								Implementation plan template
docs/SETUP.md								Setup checklist (Define configuration handling: credentials; .env.example or equivalent containing placeholders)

# Preferences
Cline (or Kilo)
C#
SQLite (then Postgres)
EFCore
React
Bun (or node.js)
DBeaver
Postman (openAPI)
ETLBox (or ETLKit)
bad data: FuzzySharp, phonetic matching, token-based, probabilistic, normalization/first-pass (lowercase, abbrev.s), ML(dedupe.io)

# prerequisites
1. .NET SDK, Node.js, Git, SQLite
2. Extensions: C# Dev Kit, ESLint, Prettier, SQLite viewer

# CLI
git init
git add .
git commit -m "Create billing enquiry API contract"

git add .
git commit -m "Integrate mock CRM and billing APIs"
git clone https://github.com/user/repo.git

dotnet build 
dotnet test 
dotnet run --project src/BillingAgent.Api      
dotnet clean 

dart run <file.dart>
dart analyze
dart test
dart fix
dart format

bun run <script or file>
bun --watch <file>
bun --hot <file>
bun test
bun build

node app.js
node --watch app.js

$env:OpenRouter__ApiKey = "key"
$env:OpenRouter__Model = "openai/gpt-5.6-sol-20260709"