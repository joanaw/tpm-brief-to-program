# CLAUDE.md: Methodology & Reasoning Log
## AI Initiative TPM Analysis | March 17, 2026

This file documents the reasoning process, judgment calls, and output structure used to produce the TPM analysis from the CPO's leadership brief. It is intended to make this methodology reusable for future runs on similar inputs.

---

## Input Characterization

**Document type:** Executive vision brief (not a project charter, not a PRD)
**Signal-to-noise ratio:** Low. The brief is heavy on intent, light on decisions
**Tone:** Directional and aspirational; several key items deferred ("TBD," "maybe," "I think")
**Risk profile:** High (unresolved legal flag, undefined scope, constrained engineering availability)

The first analytical move was to characterize *what kind of document* this was. A vision brief requires a different response than, say, a detailed spec. The job here was not to rubber-stamp the brief but to surface what's missing before execution begins.

---

## Reasoning Process

### Step 1: Identify what is stated vs. what is assumed vs. what is unresolved
Before producing any output, the brief was read with three mental filters running in parallel:
- **Stated facts:** Engineering available after end of April. Data team has related work. GDPR was flagged.
- **Assumptions being made:** Budget will materialize. Data team's work is reusable. GDPR is resolved. Q3 is achievable.
- **Unresolved decisions:** Dashboard vs. embedded. What "AI agents" means. MVP scope. Primary user persona.

This triage directly shaped the structure of the output: the open questions section is essentially the "unresolved" list, and the risks section is where stated-but-unverified items are flagged.

### Step 2: Flag unverified resolutions explicitly
The GDPR item was the most consequential judgment call. The CPO wrote "I think it was resolved", which could mean (a) it was actually resolved and the CPO forgot the details, or (b) it was not resolved and has been informally assumed away. In either case, "I think" is not an acceptable compliance posture for an ML initiative using customer data. It was elevated to the highest-severity flag in the document.

The data team "synergies" statement was similarly flagged, not as a blocker, but as an assumption that needs validation before being built into the program plan.

### Step 3: Decompose into workstreams by separation of concerns
The initiative was decomposed into workstreams using the principle of *independent deliverability*: each workstream should be able to make progress without being fully blocked by another. The five workstreams identified were:
1. Data Foundation (infrastructure layer)
2. AI/ML Intelligence (model layer)
3. Product Surface & UX (presentation layer)
4. Legal & Compliance (gates everything)
5. Program Management & Change Management (coordination layer)

The layered framing (infra → model → surface) also reflects the natural build order and dependency chain.

### Step 4: Anchor phasing to the hard constraint
The engineering availability constraint (unavailable until end of April) was treated as a hard boundary, not a soft one. Rather than trying to work around it, the phasing was designed to exploit it: Phase 0 runs *during* the engineering blackout and is scoped entirely to discovery, decision-making, and unblocking work that doesn't require engineers. This means May 1 becomes a clean, well-prepared start rather than a chaotic ramp.

### Step 5: Distinguish leading from lagging metrics
Success metrics were split into leading indicators (measurable during build, useful for course-correcting) and lagging indicators (measurable post-launch, useful for proving value). A common failure mode in AI initiatives is measuring only lagging indicators and discovering failure too late. The leading indicators here (data coverage, model precision/recall, alpha engagement) give the team early warning signals.

---

## Judgment Calls Made

| Decision | Rationale |
|----------|-----------|
| Elevated GDPR to critical/blocking status | "I think it was resolved" is not a legal clearance. ML on customer data is a high-risk data use category under GDPR. |
| Recommended churn risk as V1 use case | Highest-signal use case with the most defensible ROI story; also most likely to have labeled training data available. |
| Scoped V1 to Customer Success as primary persona | CS teams have the most direct relationship with at-risk accounts and will generate the best feedback signal for model iteration. |
| Deferred "AI agents" to post-Q3 | "AI agents" is architecturally complex and undefined. Scoping it to V1 would introduce risk without clear user value being established yet. |
| Flagged "Data Team synergies" as unverified | Reusability of data work is an assumption, not a confirmed dependency. Building on unvalidated foundations is a common program failure mode. |
| Treated budget TBD as a blocker | Architecture decisions (build vs. buy, cloud infrastructure choices) cannot be made without a budget envelope. Treating it as "will sort itself out" defers a real constraint. |

---

## v2 Addition: AI Readiness Filters (September 2026)

Added after the original analysis to cover failure modes specific to AI/ML
initiatives. This was not part of the March 2026 reasoning; it was tested
retroactively on the same brief (see Section 0 of the analysis).

### Methodology Step 3: Run AI readiness filters

*(Numbered as in the 8-step reuse pattern below, not the Reasoning Process steps above.)*

If the brief involves AI/ML, run six extra checks before decomposing workstreams.
Each one targets a failure mode that generic program planning does not catch.

| # | Filter | Question to ask | Red flag in a brief | Why it matters |
|---|--------|-----------------|---------------------|----------------|
| 1 | Problem fit | Is ML the right tool, or would rules or a simple heuristic cover V1? | The brief leads with the solution ("leverage AI") and states the problem vaguely | A solution-first brief skips the baseline. Without one, nobody can show the model adds value. |
| 2 | Data and labels | Is there a labeled outcome, how much history exists, and what is the base rate? | "We have lots of data" with no mention of outcomes | Model quality is capped by data. A metric like precision only means something relative to the base rate. |
| 3 | Evaluation defined up front | What does "good enough" mean, measured against what baseline? | Success described only as a launch date | If "good" is defined after build, it gets defined as whatever was built. |
| 4 | Autonomy level | Does the output inform, recommend, or act? Who approves actions? | "AI agents", "next best action", "proactive" | Each level up adds oversight, testing, and liability requirements. |
| 5 | Cost profile | What are the ongoing costs (inference, labeling, evaluation, monitoring, vendor fees)? | "Budget TBD" | AI costs are recurring and scale with usage, unlike a one-off build. |
| 6 | Failure impact | What happens when the model is wrong, and who is affected? | No mention of errors or edge cases | Defines how much human review is needed and which errors are acceptable. |

**Watch for the intervention trap.** If a prediction triggers an action (e.g. a CSM
calls an at-risk account and saves it), the saved account looks like a false positive
in later data. Plan a holdout group from day one, or the model's real impact can't be
measured.

**Where findings go:** Open Questions (unresolved filters), Phasing (actions that
close a gap), Success Metrics (filter 3). Where a finding is already covered elsewhere in the analysis, the
readiness table points there instead of restating it.

### Judgment Calls Added in v2

| Decision | Rationale |
|----------|-----------|
| Added a rules-based churn baseline to Phase 0 | The model needs a benchmark. If simple rules perform close to the model, V1 may not need ML. The Data Team can build it without engineers. |
| Marked precision/recall targets as placeholders | The original targets were set without a base rate or baseline, so they can't be judged yet. |
| Added a small random holdout to the Phase 2 alpha | Without it, the lagging "vs. control" churn metric has no mechanism to measure against (intervention trap). |
| Did not assume the company is B2B | The brief's account-based language suggests it, but it is not stated. Treated as an inference, not a fact. |

---

## Output Structure Used

The analysis was structured in six sections, each mapped to a distinct audience need (Section 0 added in v2):

0. **AI Readiness Check**: For the TPM and program sponsor; flags AI-specific gaps before workstreams are designed
1. **Program Breakdown / Workstreams**: For the TPM and engineering leads who need to organize work
2. **Critical Open Questions**: For the CPO and program sponsor who need to make decisions before kickoff
3. **Risks & Assumptions**: For risk owners and steering committee; flags are called out separately from general risks
4. **Proposed Phasing**: For the delivery team; respects hard constraints and provides phase-level milestones
5. **Success Metrics**: For the CPO and stakeholders; split into leading/lagging/program health

The closing summary ("Top 5 Immediate Actions") was added as a practical forcing function. Analyses that end without a clear next step tend to generate discussion but not movement.

---

## Reuse Notes: Applying This Methodology to Future Briefs

This methodology is well-suited to any **executive vision brief** that needs to be converted into an executable program plan. The core pattern is:

1. **Characterize the document type** before producing output. Vision briefs, specs, strategy memos, etc. each require different responses.
2. **Run three filters:** stated facts / assumptions / unresolved decisions.
3. **Run AI readiness filters** if the initiative involves AI/ML: problem fit, data and labels, evaluation, autonomy level, cost profile, failure impact. (Added in v2.)
4. **Flag "I think" statements** on compliance, legal, or dependency items. These are almost always unverified.
5. **Decompose workstreams by separation of concerns**, not by org chart.
6. **Anchor phasing to hard constraints first**, then fill in the rest.
7. **Split metrics into leading and lagging.** Leading indicators save programs, lagging indicators evaluate them.
8. **End with concrete immediate actions:** no more than 5, owned and time-bound.

---

## Files in This Folder

| File | Description |
|------|-------------|
| `ai_initiative_brief.md` | Original source brief from the CPO |
| `AI_Initiative_TPM_Analysis.md` | Full TPM analysis output |
| `CLAUDE.md` | This file: methodology, reasoning log, reuse guide |
| `README.md` | Project overview, methodology summary, how to reuse |

---

*Last updated: September 24, 2026 (v2: AI readiness filters). Original: March 17, 2026*
