# CLAUDE.md — Methodology & Reasoning Log
## AI Initiative TPM Analysis | March 17, 2026

This file documents the reasoning process, judgment calls, and output structure used to produce the TPM analysis from the CPO's leadership brief. It is intended to make this methodology reusable for future runs on similar inputs.

---

## Input Characterization

**Document type:** Executive vision brief (not a project charter, not a PRD)
**Signal-to-noise ratio:** Low — the brief is heavy on intent, light on decisions
**Tone:** Directional and aspirational; several key items deferred ("TBD," "maybe," "I think")
**Risk profile:** High — unresolved legal flag, undefined scope, constrained engineering availability

The first analytical move was to characterize *what kind of document* this was. A vision brief requires a different response than, say, a detailed spec. The job here was not to rubber-stamp the brief but to surface what's missing before execution begins.

---

## Reasoning Process

### Step 1: Identify what is stated vs. what is assumed vs. what is unresolved
Before producing any output, the brief was read with three mental filters running in parallel:
- **Stated facts:** Engineering available after end of April. Data team has related work. GDPR was flagged.
- **Assumptions being made:** Budget will materialize. Data team's work is reusable. GDPR is resolved. Q3 is achievable.
- **Unresolved decisions:** Dashboard vs. embedded. What "AI agents" means. MVP scope. Primary user persona.

This triage directly shaped the structure of the output — the open questions section is essentially the "unresolved" list, and the risks section is where stated-but-unverified items are flagged.

### Step 2: Flag unverified resolutions explicitly
The GDPR item was the most consequential judgment call. The CPO wrote "I think it was resolved" — which could mean (a) it was actually resolved and the CPO forgot the details, or (b) it was not resolved and has been informally assumed away. In either case, "I think" is not an acceptable compliance posture for an ML initiative using customer data. It was elevated to the highest-severity flag in the document.

The data team "synergies" statement was similarly flagged — not as a blocker, but as an assumption that needs validation before being built into the program plan.

### Step 3: Decompose into workstreams by separation of concerns
The initiative was decomposed into workstreams using the principle of *independent deliverability* — each workstream should be able to make progress without being fully blocked by another. The five workstreams identified were:
1. Data Foundation (infrastructure layer)
2. AI/ML Intelligence (model layer)
3. Product Surface & UX (presentation layer)
4. Legal & Compliance (gates everything)
5. Program Management & Change Management (coordination layer)

The layered framing (infra → model → surface) also reflects the natural build order and dependency chain.

### Step 4: Anchor phasing to the hard constraint
The engineering availability constraint (unavailable until end of April) was treated as a hard boundary, not a soft one. Rather than trying to work around it, the phasing was designed to exploit it: Phase 0 runs *during* the engineering blackout and is scoped entirely to discovery, decision-making, and unblocking work that doesn't require engineers. This means May 1 becomes a clean, well-prepared start rather than a chaotic ramp.

### Step 5: Distinguish leading from lagging metrics
Success metrics were split into leading indicators (measurable during build, useful for course-correcting) and lagging indicators (measurable post-launch, useful for proving value). A common failure mode in AI initiatives is measuring only lagging indicators and discovering failure too late. The leading indicators here — data coverage, model precision/recall, alpha engagement — give the team early warning signals.

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

## Output Structure Used

The analysis was structured in five sections, each mapped to a distinct audience need:

1. **Program Breakdown / Workstreams** — For the TPM and engineering leads who need to organize work
2. **Critical Open Questions** — For the CPO and program sponsor who need to make decisions before kickoff
3. **Risks & Assumptions** — For risk owners and steering committee; flags are called out separately from general risks
4. **Proposed Phasing** — For the delivery team; respects hard constraints and provides phase-level milestones
5. **Success Metrics** — For the CPO and stakeholders; split into leading/lagging/program health

The final section — "Top 5 Immediate Actions" — was added as a practical forcing function. Analyses that end without a clear next step tend to generate discussion but not movement.

---

## Reuse Notes — Applying This Methodology to Future Briefs

This methodology is well-suited to any **executive vision brief** that needs to be converted into an executable program plan. The core pattern is:

1. **Characterize the document type** before producing output — vision brief, spec, strategy memo, etc. each require different responses.
2. **Run three filters:** stated facts / assumptions / unresolved decisions.
3. **Flag "I think" statements** on compliance, legal, or dependency items — these are almost always unverified.
4. **Decompose workstreams by separation of concerns**, not by org chart.
5. **Anchor phasing to hard constraints first**, then fill in the rest.
6. **Split metrics into leading and lagging** — leading indicators save programs, lagging indicators evaluate them.
7. **End with concrete immediate actions** — no more than 5, owned and time-bound.

---

## Files in This Folder

| File | Description |
|------|-------------|
| `ai_initiative_brief.md` | Original source brief from the CPO |
| `AI_Initiative_TPM_Analysis.md` | Full TPM analysis output |
| `CLAUDE.md` | This file — methodology, reasoning log, reuse guide |

---

*Last updated: March 17, 2026*
