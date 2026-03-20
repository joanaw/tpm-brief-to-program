# TPM Brief to Program

A reusable methodology for converting vague executive briefs into structured,
executable program plans — using AI as a thinking partner, not a replacement
for TPM judgment.

---

## The Problem

Executive briefs are often light on decisions and heavy on intent. Words like
"TBD," "maybe," and "I think it's resolved" appear where scope, budget, and
legal clearance should be. Teams that treat these briefs as execution-ready
start building on unvalidated foundations.

The TPM's job is to make ambiguity executable — before engineering starts,
before money is spent, before assumptions become technical debt.

---

## What's In This Repo

| File | Description |
|------|-------------|
| `ai_initiative_brief.md` | A fictional CPO brief — realistic but made up |
| `AI_Initiative_TPM_Analysis.md` | Full structured program analysis from that brief |
| `CLAUDE.md` | The methodology: reasoning log, judgment calls, 7-step reuse pattern |

> **Note:** The brief used in this example is fictional — created to demonstrate the methodology. The methodology is real and generalizable to any executive vision brief.

---

## The Methodology — 7 Steps

Documented in full in `CLAUDE.md`. The short version:

1. **Characterize the document type** — vision brief, spec, strategy memo each
   require different responses
2. **Run three filters** — stated facts / assumptions / unresolved decisions
3. **Flag "I think" statements** on compliance, legal, or dependency items —
   these are almost always unverified
4. **Decompose workstreams by separation of concerns**, not by org chart
5. **Anchor phasing to hard constraints first**, then fill in the rest
6. **Split metrics into leading and lagging** — leading indicators save
   programs, lagging indicators evaluate them
7. **End with concrete immediate actions** — no more than 5, owned and
   time-bound

---

## The Novel Part — The Reasoning Log

Most TPMs share the analysis. This repo shares the meta-layer: a `CLAUDE.md`
that documents *how* the analysis was made — which judgment calls were made,
why, and how to replicate the thinking on a different brief.

This is the artifact worth studying. The analysis is one output. The reasoning
log is a reusable thinking tool.

---

## How to Reuse This

1. Take any vague executive brief
2. Read `CLAUDE.md` — understand the 7-step pattern and the judgment call table
3. Apply the three filters to your brief (stated / assumed / unresolved)
4. Use the workstream decomposition and phasing approach as a starting structure
5. Adapt the success metrics framework to your domain

AI accelerates steps 3-5 significantly when given the right context. The
judgment in steps 1-2 remains human.

---

## TPM Context

This methodology maps directly to core TPM competencies:

- **Ambiguity resolution** — converting "let's make it happen" into a program charter
- **Risk identification** — surfacing blockers before they become crises
- **Stakeholder alignment** — structured open questions force decisions that
  would otherwise be deferred
- **Cross-functional coordination** — workstream decomposition by separation of
  concerns, not org chart

The pattern scales: platform migrations, vendor evaluations, org restructuring,
regulatory programs — any domain where a senior leader has a vision and a team
needs to execute it.

---

## Author

Built by Joanna — TPM specialising in AI/ML, agentic workflows, and AI Safety
operations. Exploring what it means to make AI ambiguity executable.

[AgentRed-Light](https://github.com/joanaw/agent-red-light) — a related
project: guardrail test suite for AI agents.
