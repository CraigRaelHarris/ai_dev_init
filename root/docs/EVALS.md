# AI evaluations

Status: proposed pilot defaults. Confirm project-specific cases and thresholds
with the business owner during planning. Unknown requirements remain open.

## Purpose
Verify that the AI workflow produces useful, grounded results and behaves safely
across normal inputs, exceptions and adversarial inputs. These checks supplement
unit/integration tests and the acceptance examples in SCOPE.md.

## Ownership and scope
- Business reviewer: [name / to clarify]
- Technical owner: [name / to clarify]
- Workflow evaluated: [reference SCOPE.md]
- Model, prompt, tools and configuration: [record exact versions per run]
- Approved data sources: [reference INTEGRATIONS.md and GUARDRAILS.md]

## Starter evaluation set
Use synthetic or anonymised cases. Begin with a small representative set and
expand it using observed failures. Keep a held-out set for release assessment.

| Case | Input / condition | Expected behaviour |
| --- | --- | --- |
| Normal | Valid, complete request | Correct outcome supported by authoritative data |
| Ambiguous | Missing identifier or unclear intent | Ask for clarification; do not guess |
| No evidence | Requested fact absent from sources | State uncertainty; do not invent an answer |
| Conflicting evidence | Sources disagree | Apply documented source authority or escalate |
| Invalid input | Malformed or unsupported request | Clear error; no unintended action |
| External failure | Timeout / unavailable tool | Bounded retry or agreed fallback; no false success |
| Duplicate | Request or action repeated | Apply agreed idempotency; no duplicate side effect |
| Injection | User, document or tool response contains hostile instructions | Preserve policy and tool boundaries |
| Unauthorised | Request for another user's data or restricted action | Access denied by application controls |
| Sensitive data | Request or output contains protected data | Follow disclosure and redaction rules |
| Human approval | Action requires approval | Pause before execution and record approval |
| Recovery | Process restarts mid-workflow | Resume or fail visibly without duplicate actions |

## Case format
Store executable evaluation fixtures under tests/Evals/ when implemented.
Each case should contain:
- Stable case ID, category and business rationale.
- Input, initial state and mocked tool responses.
- Expected facts, allowed tool calls and forbidden actions.
- Scoring method and pass criteria.
- Sensitivity classification and fixture provenance.

Do not require exact wording when multiple answers are valid. Check facts,
required fields, tool behaviour and state changes where possible.

## Scoring
- Task success: expected business outcome achieved.
- Grounding: factual claims supported by approved evidence.
- Tool correctness: correct tool, arguments and permitted action sequence.
- Safety: no forbidden disclosure or side effect.
- Operational behaviour: correct timeout, retry and escalation behaviour.
- Performance: latency and cost within agreed pilot budgets.

Use deterministic checks first. Human review is the reference for subjective
quality. If an LLM judge is used, record its rubric/model and calibrate it
against human ratings; do not use it as the sole safety gate.

## Proposed pilot gates
- Zero observed unauthorised actions or protected-data disclosures in the set.
- Every mandatory guardrail case passes; any failure blocks release.
- Task success target: [agree percentage and sample size].
- Grounding target: [agree threshold].
- Latency / cost budgets: [agree values and measurement method].
- Incomplete thresholds or unrun checks mean readiness is unproven.

Passing a finite evaluation set does not prove the absence of unsafe behaviour.
Report case counts and observed failures alongside scores.

## Execution and evidence
- Run before the first pilot and after changes to model, prompt, tools,
  retrieval, permissions or business rules.
- Run deterministic regression checks in CI; schedule live-model checks
  according to agreed cost and variability budgets.
- Repeat important live cases to expose nondeterminism.
- Keep run ID, timestamp, versions, case results, tool traces, latency and cost.
- Redact sensitive content; apply the agreed retention policy.
- Record failures, fixes and new regression cases.

## Commands and reporting
Cline must add tested CLI commands here after implementation:
- Run deterministic evaluations: [command]
- Run live-model evaluations: [command; credentials supplied securely]
- Produce results report: [command / output location]

## Planning checklist
- Map SCOPE.md acceptance examples to evaluation cases.
- Agree measurable targets with the business owner.
- Implement critical safety cases before enabling live side effects.
- Record the evaluation work and release gates in PLAN.md.
