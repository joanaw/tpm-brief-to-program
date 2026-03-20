# AI-Powered Customer Intelligence Initiative
## TPM Program Analysis — March 17, 2026

---

> **Document context:** This analysis is based on the CPO's leadership brief dated March 17, 2026. Several inputs in the brief are unverified or underspecified; those are called out explicitly throughout.

---

## 1. Structured Program Breakdown — Proposed Workstreams

The initiative as described maps naturally to five parallel workstreams. Each requires a dedicated lead and has distinct dependencies.

---

### Workstream 1: Data Foundation & Integration
**Goal:** Establish a reliable, governed data layer that consolidates customer signals across all source systems.

- Audit existing data sources (support tickets, usage telemetry, churn signals, NPS responses, CRM data)
- Inventory what the Data Team has already built — identify reusable pipelines, schemas, and models
- Define data contracts and ownership for each source system
- Design and build unified customer data model / feature store
- Establish data quality SLAs and monitoring

**Key dependency:** Access to source systems, confirmation of data team's work scope, legal clearance on data use.

---

### Workstream 2: AI/ML Intelligence Layer
**Goal:** Build the models and agent logic that power proactive intelligence (churn risk, expansion signals, next-best-action).

- Define model requirements for each use case (churn prediction, expansion opportunity scoring, NBA recommendation)
- Evaluate build vs. buy vs. API (e.g. off-the-shelf ML platforms vs. custom models)
- Define what "AI agents" means in this context — autonomous actions vs. recommendations vs. alerting
- Train, evaluate, and iterate on baseline models
- Design feedback loops to improve model accuracy over time

**Key dependency:** Workstream 1 must deliver a clean data layer before model training can begin in earnest.

---

### Workstream 3: Product Surface & UX
**Goal:** Determine where and how intelligence surfaces to end users (product managers, sales reps, CS teams).

- Decide: dedicated dashboard vs. embedded in existing tools (CRM, CS platform, internal tools) — this is currently unresolved
- Define personas and primary use cases per audience (product team, sales, customer success)
- Design and validate UX with target users before build
- Implement front-end surface(s)
- Build notification / alerting mechanism for proactive flags

**Key dependency:** Requires product decisions that are currently open (see Section 2).

---

### Workstream 4: Legal, Privacy & Compliance
**Goal:** Ensure the initiative is legally compliant before any data is ingested or any model is trained.

- Resolve and document the GDPR flag raised by Legal ⚠️ **[UNVERIFIED — see flag below]**
- Review data retention, processing, and consent requirements for each data source
- Assess whether customer data used for ML model training requires consent updates
- Define data handling policies for AI-generated outputs (e.g. can a churn score be shared with Sales?)
- Confirm compliance posture for any third-party AI/ML services used

**Key dependency:** Must be resolved in Phase 0. This workstream gates everything else.

---

### Workstream 5: Program Management, Enablement & Change Management
**Goal:** Keep the program coordinated and ensure teams actually adopt the output.

- Stand up governance cadence (weekly WS leads sync, bi-weekly steering)
- Define and track milestones, owners, and dependencies across workstreams
- Develop internal rollout plan for each target persona
- Create feedback channels post-launch to capture signal for iteration
- Define escalation paths for budget, scope, and timeline risks

---

## 2. Critical Open Questions — Must Be Answered Before Execution

These are blockers. Work should not begin on dependent workstreams until these are resolved.

**Program & Scope**

1. **What is the MVP?** "Something in market by Q3" is not a scope statement. What is the minimum set of capabilities that constitutes a successful Q3 launch? One use case? One user persona? One data source?
2. **Who are the primary users for V1?** Product team? Sales? Customer Success? Prioritization drives architecture, UX, and data requirements.
3. **Dashboard or embedded — or both?** This is a significant build decision. It needs an owner and a decision by end of Phase 0.
4. **What does "AI agents" mean here?** Fully autonomous agents taking actions? Recommendation surfaces? Alert systems? This has major implications for complexity, cost, and risk.

**Engineering**
5. **How many engineers are available after the v2.0 release, and what are their skill sets?** "Available after end of April" is not a headcount or composition. Do we have ML engineers? Data engineers? Front-end engineers?
6. **Is the end-of-April v2.0 date firm?** Any slippage directly compresses the already-tight Q3 window.

**Data & Infrastructure**
7. **What exactly has the Data Team built?** Are their pipelines production-ready and reusable, or are they exploratory prototypes? This determines whether we're building on a foundation or starting fresh.
8. **Do we have confirmed access to all proposed data sources** (support tickets, usage data, NPS, churn signals)? Who owns each system and what are the integration requirements?
9. **What is the data freshness requirement** for the intelligence layer? Real-time, near-real-time, daily batch?

**Legal & Compliance**
10. **What specifically did Legal flag re: GDPR, and is it actually resolved?** (See flag in Section 3.) This is a hard blocker.
11. **Does using customer behavioral data to train ML models require updated consent language or DPAs?**

**Budget & Resources**
12. **What is the budget?** "TBD but this is a priority" is not a budget. Third-party ML tooling, cloud infrastructure, and potential vendor costs need a number before architecture decisions can be made.
13. **Are there dedicated PM and design resources,** or is this expected to run on engineering bandwidth alone?

---

## 3. Identified Risks and Assumptions

### ⚠️ Flags — Stated as Resolved but Unverified

**GDPR / Legal issue**
> *"Legal flagged something about GDPR a few weeks ago but I think it was resolved."*

This is the highest-risk statement in the brief. "I think it was resolved" is not a resolution. An unresolved GDPR issue could mean:
- Certain data sources cannot be used for ML training without consent updates
- Customer data cannot be shared across internal teams (e.g. churn scores to Sales) without policy changes
- Third-party processors (ML platforms) require updated DPAs

**Required action:** Get written confirmation from Legal that the specific issue has been closed, what the resolution was, and whether any data use restrictions remain. Do not ingest customer data or begin model training until this is in writing.

**Data Team "synergies"**
> *"The data team has been working on some related stuff already so there may be synergies there."*

"May be synergies" is an assumption, not a confirmed dependency. If the data team's work is exploratory or scoped differently, building on it could introduce technical debt or delay.

**Required action:** Conduct a structured data team discovery session in Phase 0 to inventory actual artifacts, assess production-readiness, and identify true overlap.

---

### Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Engineering slippage on v2.0 pushes availability past April | Medium | High | Identify minimum viable eng. team that can begin Phase 0 work before v2.0 ships |
| GDPR issue resurfaces as unresolved, blocks data use | Medium | Critical | Legal sign-off required before any data ingestion |
| Scope creep from "dashboard + embedded + AI agents" expands to unmeetable Q3 deadline | High | High | Hard MVP definition with CPO sign-off in Phase 0 |
| Data quality is poor — support tickets unstructured, usage data incomplete | Medium | High | Data audit in Phase 0; set realistic expectations before build begins |
| Data Team's work is not reusable at production quality | Medium | Medium | Discovery session; don't plan around this until confirmed |
| No budget approval causes mid-program stop | Medium | Critical | Escalate budget TBD to blocker status immediately |
| AI agent approach introduces unexpected complexity and safety requirements | Low-Medium | High | Define "agents" concretely before architecture; consider scoping V1 to recommendations only |
| Internal adoption failure — teams don't use the output | Medium | High | Include target personas in design process; define change management plan |

### Assumptions (currently unvalidated)

- Engineering will be fully available and appropriately skilled after end of April
- The Data Team's existing work is materially reusable
- Q3 means end of Q3 (September), not beginning (July) — this matters significantly for phasing
- There is sufficient labeled historical data to train meaningful churn/expansion models
- Product, Sales, and CS teams are aligned on what "customer intelligence" means to them
- The initiative has executive sponsorship beyond the CPO (budget owner, eng. sponsor, legal)

---

## 4. Proposed Phasing — Engineering Availability Constraint Respected

Given that Engineering is unavailable until end of April, the program has roughly **4.5 months** from May 1 to a Q3 (end of September) ship. That is workable — but only with a tightly scoped MVP and Phase 0 groundwork starting immediately.

---

### Phase 0 — Discovery & Unblocking (Now → April 30)
**Who does this:** PM, TPM, Data Team, Legal, Design (no eng. required)
**Goal:** Resolve every open question and blocker so engineering can hit the ground running May 1.

- [ ] Get written GDPR resolution from Legal
- [ ] Lock MVP scope with CPO (one use case, one persona for V1)
- [ ] Conduct Data Team discovery — inventory artifacts, assess reuse
- [ ] Confirm data source access and integration requirements
- [ ] Get engineering headcount and skill set confirmed for May
- [ ] Secure budget approval
- [ ] Begin UX discovery with target personas (product, sales, CS)
- [ ] Define data model and architecture direction
- [ ] Make dashboard vs. embedded decision

*Deliverable: Program charter with locked scope, architecture direction, legal sign-off, and eng. plan.*

---

### Phase 1 — Foundation (May 1 → May 31)
**Who does this:** Data engineers, ML engineers, backend engineers (full team now available)
**Goal:** Build the data layer and baseline model(s) for V1 use case.

- Build / adapt unified customer data pipeline
- Instrument data quality monitoring
- Train and baseline V1 model (e.g. churn risk — highest signal, most direct value)
- Stand up backend API for intelligence outputs
- Begin front-end scaffolding (dashboard or embedded integration surface)

---

### Phase 2 — MVP Build (June 1 → July 31)
**Goal:** Shippable V1 product with one core intelligence use case, accessible to internal users.

- Complete front-end surface for V1 (churn risk dashboard or embedded signal)
- Proactive alerting / notification for at-risk accounts
- Internal alpha with Customer Success team (highest-value initial user)
- Feedback loop instrumentation
- Iterate on model accuracy based on CS team input
- Security and compliance review before broader rollout

---

### Phase 3 — Expanded MVP & Hardening (August 1 → September 30)
**Goal:** Expand to additional personas/use cases, harden for production, broader internal rollout.

- Add expansion opportunity scoring (second use case)
- Extend to Sales and/or Product personas if validated in Phase 2
- Performance optimization and SLA establishment
- Documentation, training, and change management for broader rollout
- "In market" Q3 milestone hit by end of September

---

### Post-Q3 — Iteration & Roadmap
- Next-best-action recommendations
- AI agent layer (if scoped to a clear, safe, bounded use case)
- External-facing customer-visible features (if applicable)

---

## 5. Suggested Success Metrics

### North Star
**Reduction in time-to-insight for customer-facing teams** — the core value proposition is that Product, Sales, and CS learn about customer risk and opportunity faster than they do today.

---

### Leading Indicators (measurable during build)

| Metric | Target |
|--------|--------|
| Data coverage: % of customer accounts with complete signal profiles | >80% of accounts have ≥3 signal types by Phase 1 end |
| Model precision/recall for churn prediction (internal evaluation set) | Precision >70%, Recall >65% at launch |
| Data pipeline reliability | >99% uptime, latency SLA met |
| Alpha user engagement rate | >60% of CS team accessing intelligence surface weekly |

---

### Lagging Indicators (measurable 60–90 days post-launch)

| Metric | Target |
|--------|--------|
| Churn rate for accounts flagged and actioned vs. control | Statistically significant improvement vs. baseline |
| Expansion revenue influenced by AI-surfaced opportunities | Tracked and reported; target to set once baseline established |
| Time CS team learns of at-risk account (before vs. after) | Reduce average detection lag by ≥50% |
| NPS for internal users (product, sales, CS) of the intelligence surface | >7 average score |
| % of at-risk flags that receive a CSM action within 5 business days | >70% |

---

### Program Health Metrics

| Metric | Target |
|--------|--------|
| Phase 0 blockers resolved by April 30 | 100% of P0 blockers closed |
| Engineering ramp time after April 30 | Full productive capacity within 1 week |
| Scope changes requiring CPO re-approval | Tracked; minimize; any changes go through formal change control |

---

## Summary — Top 5 Immediate Actions

1. **Get Legal to produce written confirmation** of the GDPR issue status. This is the single highest-risk unresolved item.
2. **Schedule a scoping session with the CPO** to define what "in market by Q3" means concretely — one use case, one persona, one surface.
3. **Conduct a Data Team discovery session** to inventory what exists and what is production-ready.
4. **Escalate budget TBD to a blocker.** Architecture and vendor decisions cannot be made without a number.
5. **Confirm engineering headcount and skill set** for May 1 availability — number of engineers, ML vs. data vs. FE composition, and whether v2.0 date is firm.

---

*Prepared by: TPM Office | March 17, 2026*
