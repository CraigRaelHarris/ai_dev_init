Read README.md, DISCOVERY.md, SCOPE.md, DECISIONS.md, docs/INTEGRATIONS.md, docs/PLAN.md, docs/SETUP.md, docs/EVALS.md, docs/GUARDRAILS.md and .clinerules/project.md.
Help me plan this client solution using [C# ASP.NET Core, React/TypeScript and SQLite/EF Core]. Treat this stack as proposed and flag any material mismatch.
First identify missing information that changes scope or behaviour. Separate blocking questions from assumptions we can safely validate during the pilot.
Keep your questions and explanation brief. Identify gaps.
Then propose the simplest design and delivery sequence covering project structure, database/state, integration mocks, manual exception handling, authentication, errors, logging, tests and deployment. Define the first useful end-to-end workflow and how we will demonstrate it against acceptance examples.
Do not generate application code yet. Present the plan for review. Once agreed, record it in docs/PLAN.md and decisions in DECISIONS.md using a mode that permits file edits. Then scaffold and verify the skeleton before business features.

After scaffolding, update README.md with a "## Run" section containing the exact CLI commands to restore dependencies, configure required settings, apply database migrations, seed development data, and start the API and frontend.

State the working directory for each command, whether separate terminals are needed, and the expected local URLs/ports. Verify the commands work before documenting them. Include a single command to start everything if practical.

Read docs/EVALS.md and docs/GUARDRAILS.md. During planning, adapt both to this project's workflow, identify unresolved decisions, and include their implementation and verification in docs/PLAN.md.

PROJECT SETUP REQUIREMENTS
==========================

STACK
-----
- Runtime: ASP.NET
- Frontend: React
- Database: SQLite (bun:sqlite)
- Language: TypeScript


API CONVENTIONS (v1)
---------------------

OpenAPI Spec
- Ship an OpenAPI 3.1 spec at openapi.yaml in the repo root.
- Every operation MUST have:
  - operationId (used as Postman request name)
  - tags (drives Postman folder structure; group by resource, not method)
  - examples on request bodies and responses
- Declare securitySchemes in components even if auth is off.
- servers must use a {{baseUrl}} variable.

Error Format
All error responses MUST use this exact shape:

{
  "error": {
    "code": "MACHINE_READABLE_CODE",
    "message": "Human-readable description",
    "details": [
      { "field": "field_name", "issue": "reason" }
    ]
  }
}

- Use correct HTTP status codes: 400, 401, 404, 409, 422, 500.
- Never return 200 for errors.

Auth (v1)
- No auth on localhost during development.
- If auth is needed: single X-API-Key header, no OAuth/JWT.

Endpoints
- GET /health -> 200 with {"status":"ok"}
- GET and PUT must be idempotent.
- POST endpoints must be safe to call repeatedly in dev (auto-cleanup or a POST /reset that wipes and reseeds the DB).

Content
- Content-Type: application/json on all request/response bodies.
- No form-encoded, XML, or protobuf.


POSTMAN COMPATIBILITY CHECKLIST
-------------------------------
[ ] openapi.yaml imports cleanly into Postman (one-click, no manual fixes)
[ ] Every request has a pre-filled example body
[ ] Auth is configured at collection level (or absent)
[ ] {{baseUrl}} collection variable is set
[ ] One reusable test script works across all endpoints (checks status code + error shape)
[ ] Collection runner can execute the full suite without manual intervention


FILE STRUCTURE (suggested)
--------------------------
/
├── openapi.yaml
├── bunfig.toml
├── package.json
├── src/
│   ├── index.ts          # entry point, starts server
│   ├── routes/
│   │   ├── health.ts
│   │   ├── users.ts
│   │   └── ...
│   ├── db/
│   │   ├── index.ts      # bun:sqlite connection
│   │   └── schema.sql
│   └── types/
│       └── api.ts        # shared request/response types
├── public/               # React build output
└── README.md


DEFINITION OF DONE (v1)
-----------------------
1. bun install && bun dev starts the full app (API + React) on one port.
2. openapi.yaml is valid and imports into Postman with zero manual edits.
3. GET /health returns 200.
4. At least one CRUD resource (e.g., /users) is fully functional with structured errors.
5. POST /reset clears and reseeds the database.
6. No external services required (everything runs locally).   
