Outcome → current workflow → evidence and sources of truth → MVP scope → technical decisions → validation → pilot path
WHY, WHAT, HOW

#Challenge the initial solution request.
	“Before deciding that an autonomous agent is the answer, I’d like to understand where the delay and cost actually occur.”
#Ask for concrete cases.
	Request one normal example, one failed example and one high-risk exception.
#Establish measurable value.
	Ask for the baseline, target, measurement method and result that would justify continuing.
#Map the real workflow.
	Identify the trigger, completion event, users, handoffs, delays and manual workarounds.
#Assign sources of truth.
	Explicitly determine which system owns every critical fact.
#Expose disagreement and uncertainty.
	Never silently choose between conflicting systems or infer missing information.
#Separate AI from deterministic controls.
	AI may classify, summarize or draft; identity, money, permissions, eligibility and critical calculations usually remain controlled by code and business rules.
#Define autonomy carefully.
	Clarify whether the system may read, recommend, draft, update, transact or communicate externally.
#Cover failure behaviour.
	Include timeouts, retries, duplicates, stale data, dependency outages, human handoff and recovery.
#Choose a genuinely vertical slice.
	One trigger → real data retrieval → one useful action → deterministic checks → audit record → safe failure or escalation.
#Make requirements observable.
	Replace “fast” with a latency target and “accurate” with defined acceptance cases and thresholds.
#Move forward despite uncertainty.
	Say: “I’ll assume X for the slice. If Y proves true, I would change Z. The first validation action is…”
	
Completeness check
	- Customer problem and measurable outcome are explicit.
	- Normal and high-risk exception journeys are covered.
	- Sources of truth are assigned; CRM/billing conflict is not hidden.
	- Assumptions and evidence requests are separated from decisions.
	- MVP boundary and exclusions are explicit.
	- Data-quality, privacy, permissions, audit, failure, retry, and human-review behaviour are specified.
	- Requirements are observable and testable.
	- The first checkpoint is a thin, useful, end-to-end slice.
	- Open questions have owners, dates, and stated consequences.

“So far, the target is to reduce [business problem] for [specific users]. The safety boundary is [prohibited outcome or action]. For the proof of concept, I propose we test [one end-to-end journey], using [authoritative source], with [human-review condition]. We’ll consider it promising if [measurable result] is achieved.”



